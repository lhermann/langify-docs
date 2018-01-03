# Langify

Documentation for the open translation system Langify

Langify is under development. You may have a look at our status quo below. Feel free to share your thoughts in the _issues_ section.

## Mission

To provide an online platform for books and articles to be read and translated easily into another language by volunteers sharing the same passion, working together to produce a result that has uniform language, high quality and high fidelity to the original.

## Vision

To translate all of EGW's writings into every language currently in wide use, especially where paid translators cannot be afforded.

## Core features

Edior, social components.


## Principles

Our focus in development.


## Translations

There will be one translation for each langauge. It will be defined in which locale it should be written.

Future plans: We might add one translation per locale (e.g. British and American English). We might also allow two translations, one which is very exact and one which emphasizes a beautiful language (we also have e.g. different bible translationsfor that reason).


## Accounts

**Username**: Publicly visible, therefore don't use your e-mail address.

**First and last name**: Your real name. Please understand that official translations need official names. You can choose between _public_, _contributors_ and _reference_. When you select _contributors_ it is visible to registered contributors, when you select _reference_ it is used for reference, e.g. in printed books, only.


## Versioning

[Editions, releases and drafts](versioning.md).

## Authorization and reward system

[Read](authorization.md) about reputation, badges and privileges in order to produce high quality translations.

## Formats

[Which](formats.md) formats may be used.


## API

[See](api.md) our API URL structure.


## Technologies

Tools our website is built with:

Function | Name
---------|-----
Front end (SPA) | [Vue.js](https://vuejs.org/)
Backend (ORM, web framework, admin) | [Django](https://www.djangoproject.com/)
REST API | [Django REST framework](http://www.django-rest-framework.org/)
Database | [PostgreSQL](https://www.postgresql.org/)
Languages | JavaScript, Python (and others like HTML, CSS)


## Examples

[What](examples.md) inspired us.

## Questions & Answers

1. Who is translating?
    - Everybody with good english skills is encouraged to contribute.
2. How are the translations financed?
    - Our contributors are encouraged to work voluntarily. The plattform (running costs, maintenance) is supported either by donations (EGW Estage, ...) or by allowing Authors to use our plattform for a fee.
3. What is the motivation for translators to volunteer?
    - We are counting on the duty our members feel toward God and his cause to volunteer their time. This motivation depends upon the finished translations being able to be used freely without restricting licenses (due to publishing house contracts for example).
4. How does the collaboration work?
    - Collaboration works similar to a Google Drive Document where everybody is able to work simultaniously on the same text. A history of each change is kept. Each paragraph/segment of the text needs to be peer-reviewed and approved. An easily acessible communication option encourages translators to work together on difficult passages. A reward system encourages translators to continually improve on existing translations. See [authorization and reward system](authorization.md)
5. What ensures uniform language?
    - The platform will provide an easy-to-access glossary with explanations provided by the publisher together with a list how the word was translated in other places. See also question 4.
6. What ensures hight quality?
    - Translators are encouraged to continually improve on their and other people's translations. Each paragraph has to be peer-reviewed and approved. See [quality assurance](quality_assurance.md) and also question 4.
7. What ensures high fidelity to the original?
    - A glossary, maintained by the publisher, explains words and lists prior translations of the same. The publisher has the option to review the finished translation by someone trusted (e.g. an Adventist university).
8. Who decides whether a translation is finished?
    - Once all paragraphs are approved (see question 4) a majority consensus of all active translators can release the translation as a whole. Still then improvments on the text are encouraged and can under consensus be released as Edition 2, 3, etc. The publisher can reserve the right to make the final decision, however the publisher has to produce valid points if a translation is not released in order to prevent frustration on the side of the translators.
9. What happens when a translation is finished?
    - The translation will be taged with a version number (e.g. Edition 1). Digitally accessible formats will automatically be generated (e.g. PDF, MOBI, EBOOK, ...). The text will be available for online reading and is exposed through a public API. See [versioning](versioning.md), [API](api.md) and [formats](formats.md).
10. Under which licenses will translations be?
    - If possible a Creative Commons license allowing for free non-commercial use. Translations that were financed by the publisher grand some pay to the translators wherefore the publisher can freely choose the lisence. See [licenses](licenses.md).
11. Who is allowed to physically publish a translation?
    - Translations with a Creative Commons license can be printed by anybody for personal use or free distribution. Contracts for commercial publishing are as yet undefined.
12. What are the development costs and timeframe?
    - The timeframe for releasing the first major version is mid 2019. Total development cost will amount to 50,000 USD. Time and costs are needed to solve all tecnical problems and to test all points mentioned in the answer to question 4 on real poeple and iterate this process.
