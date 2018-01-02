# Architecture

This article describes our software packages and how they interact with each other.

As a general rule you can say we choose packages which best fit our needs, are resource protecting (fast, low CPU usage, low memory usage, low bandwidth usage), are well maintained, are secure and reliable, are easy to use for developers, can be adjusted easily and use new technologies.

## Client (User)
We decided to use a new technique called single-page application (*SPA*).

### SPA

This means you visit our website and the browser loads basically three files (in reality there a few, less important more):
1. a small file containing *HTML* (*Hypertext Markup Language*, the standard markup language for creating web pages),
2. a file containing *JavaScript* (a programming language) and
3. a file containing *CSS* (*Cascading Style Sheets*, used for describing the presentation of a document).

These files are always the same, no difference which URL (*Uniform Resource Locator*, colloquially termed a web address) you enter. Now your browser runs the JavaScript code. The code looks up the URL you entered, requests needed data from the server (see section *API*) and builds the proper HTML for that page. As a result your browser is able to render the page (together with the styling information of the CSS file). If you click somewhere the HTML will be updated by the JavaScript code. The same is happening when you enter text, etc.

#### Pros and cons
The advantage of this method is that the server has to send and receive data only (except for the first time) and as a result we reduce data traffic. The user sees the pages load quicker and the server is able to handle more requests.

Disadvantage: Different browsers have different capabilities to run JavaScript. 

#### Packages
The software for our SPA is called [*Vue.js*](https://vuejs.org/) (pronounced like *view*). Our editor (which you hardly recognise as one) is the [*MediumEditor*](https://yabwe.github.io/medium-editor/). We use [*webpack*](https://webpack.js.org/) to create the three mentioned files from source files and [*Node.js*](https://nodejs.org/en/) and [*npm*](https://www.npmjs.com/) to manage all the pure frontend packages.

### The usual way

We use the SPA with one exception to a standard user: All pages of our website where you have to enter your password are not served by our SPA but by *Django* (see below) directly for security reasons. (A malicious hacker can sniff data more easily using JavaScript. Nevertheless we might change that in the future.)

This means we use the usual method here: A user types in a URL, the request reaches the server, the server renders the HTML and sends it back. Then the browser has to request appropriate CSS and and maybe JavaScript files. (The HTML file is bigger with the data already included at the right place, JavaScript files are smaller because they do little display updates only.)

## Server

The server is the central computer where user requests go to, are processed, stored and responses are sent back to the user. It's operating system is Linux with many software packages. I’ll pick out the most interesting concerning our website.

### Webserver

The web server is the software which is responsible for HTTP requests and responses. I.e. when you type our domain in your browser and hit return this request arrives at the web server. Then it is processed (by other software) and finally the web server sends back a response to your browser and you (should) see what you asked for.

We are running several web servers in different layers:

#### nginx
Here all requests arrive.

Static files are generally served by [*nginx*](https://nginx.org/en/) (pronounced ˌɛndʒɪnˈɛks) directly because it is optimised for that. Static files don’t change all the time and include images, fonts, Javascript files and CSS files.

#### uWSGI/Daphne
Requests with varying responses (depending on e.g. who sends it or with just changing content) are something else. They are passed on to another web server which knows how to interact with our web framework (*Django*). We are currently using [*uWSGI*](http://uwsgi-docs.readthedocs.io/en/latest/) for that purpose. We probably will use [*Daphne*](https://github.com/django/daphne/) (at least additionally) in the future because our aim for our translators is to get real time updates from other translators. *Daphne* is able to do this more resource protecting with protocols called *WebSocket* and *HTTP2*. (The main advantage for us is that the user’s browser doesn’t have to ask every second if there is an update but the server will just send updates to the browser (without a request).)

### Storage

Here we save the data users send us. We distinguish thee types:

#### Files
This is equal to the directories and files you know from your computer. Here we store images, import and export files. Files are served by *nginx*.

#### Database
Here we store texts, user permissions, relations between all these objects and other stuff. An example: Every paragraph of a book is one database object. It has relations to e.g. the general information of the book (an object with title, language, description, etc.), the original or translated passage and the history. As you can see this content may change frequently.

The database is stored on hard drive. We use [*PostgreSQL*](https://www.postgresql.org/).

#### Cache
Caching is an important technique to protect resources, serve content quicker (approx. 10 times) and let our users work more fluently. We will cache most of the currently used content of the database (and results depending on it). Cache is stored in memory (RAM) and can’t be used as single storage system for that reason. (You would loose all data at a server crash.) We probably will use [*Redis*](https://redis.io/).

### Processing

#### Web framework
[*Django*](https://www.djangoproject.com/) accepts the requests and sends back responses accordingly.

#### Application programming interface (API)
We need an API because we decided to use a single-page application design. Frontend and backend meet at the API. Both know how to „speak this language“. Information is transferred in the *JSON* (JavaScript Object Notation, pronounced dʒeɪsən) format in our API.

We might also have a public API in the future to allow third party programs and websites to use our content.

If there comes an API request Django uses a package called [*Django REST framework*](http://www.django-rest-framework.org/) to handle it.

#### Conversion
We have to import the works to be translated and want to export the translations.

##### Import
Currently we receive books in the JSON format. We have to analyse and convert them in order to reflect the correct layout (e.g. a heading should be displayed as a heading and a reference as reference). We use [*BeautifulSoup*](https://www.crummy.com/software/BeautifulSoup/) for this task. Finally we save it in the database (using Django’s ORM = object-relational mapper).

##### Export
We want to provide [different formats](formats.md#export) of the releases. We might use *BeautifulSoup* and parts of [*Calibre*](https://calibre-ebook.com/) to reach this goal.

#### Permissions
This is a very complex topic. We are currently using *Django* and *Django REST framework* for the prototype but might need [*django-guardian*](https://django-guardian.readthedocs.io/en/stable/overview.html) to refine it. It provides own permissions for every database object. E.g. you have one translation in Spanish (= one database object) and one in Afrikaans (= another database object). User A is a native Spanish speaker and has translation rights for the Spanish project but should not have these rights for Afrikaans.

#### History
You can track edits on our website. *Django* brings the basic functionality and the specialised package is called [*django-simple-history*](https://django-simple-history.readthedocs.io/en/latest/). It automatically creates a new history database object for each edit.

#### Signup
Signup should be easy and in order to prevent confusion and guarantee credibility we want to make sure that users enter their real data.

We want to use a tool which knows all the cities of the world and adjusts the form according to the country. We might use [*GeoNames*](http://www.geonames.org/)’s data and [*django-cities*](https://github.com/coderholic/django-cities) or a similar package for that. Django includes a „world-class geographic Web framework“ called *GeoDjango* for this task.

Another thing is validation of the address. Here might [*Mapbox*](https://www.mapbox.com/) (alternative to *Google Maps*) come in as SaaS.

#### Validation
We use *HTML* to store the translations. This requires careful validation. Otherwise a security hacker was able to use our website to display malicious HTML or even JavaScript to other users. For that reason we take the HTML apart using *BeautifulSoup* and check everything to match our targets.

Validation of import data is done equally. Validation of user data is discussed in the prior section.

## Software as a Service (SaaS)
SaaS (pronounced sæs) means for our website that we send content to another website. That website processes it and sends something back, stores it or sends a notification to us.

### Spell and grammar checks
We might use [*LanguageTool*](https://www.languagetool.org/) for that task.

### Error tracking
It is important that we are informed about appearing errors and get as much information about the circumstances as possible to be able to quickly solve it. Users normally don’t inform you if something goes wrong. They just leave the page and keep the bad user experience in mind. Currently we get error reports from both, the frontend and the backend. We use [*Sentry*](https://sentry.io/) to manage the error reports.

### Address validation
We might use [*Mapbox*](https://www.mapbox.com/) to validate addresses.

### Development platform
We use [*GitHub*](https://github.com) to host and review our code and documentation in all the different versions, discuss issues, report the current status of bugs and plan for the future.

## Development
There are many tools we use but I skip this part for now.

## Glossary

### Frontend

This is the presentation layer, the part of the website the users see. You could also define it as the scripts that run at the client-side. You could say it is equal to *Vue.js* concerning our website (and at some places *Django*).

As a result the frontend is mainly written in *JavaScript*.

### Backend

This is the data access layer, the part the users don’t see. The stuff that is done server-side. The administrative views (managed by *Django*) are also part of the backend.

*Python* is the dominating language here (at least for our website project).
