# Langify REST API

Documentation of URLs and their allowed methods. For the JSON objects see API OPTIONS directly.

`HEAD` and `OPTIONS` are not listed here.

Under development. Please use the URLs provided in the JSON!

## Private

This API is for use between front- and backend.

**Note:** Please let me know if you need the information of several JSON objects on one page frequently. We will combine them in order to reduce queries.

### Works

Prefix: `api/`

URL | Content | Methods
----|---------|--------
`o/` | List of original works | GET, POST
`o/<ID>/` | Specific original work | GET, PUT, PATCH, DELETE
`o/<ID>/s/` | Sections of a work | GET, POST
`o/<ID>/s/<position>/` | Specific section | GET, PUT, PATCH, DELETE
`t/` | List of translated works | GET, POST
`t/<ID>/` | Specific translated work | GET, PUT, PATCH, DELETE
`t/<ID>/s/` | Sections of a work | GET, POST
`t/<ID>/s/<position>/` | Specific section | GET, PUT, PATCH, DELETE

## Public

A public API is planned.

## Ideas

### Works

Prefix: `api/`

URL | Content | Methods
----|---------|--------
~~`works`~~ | All works | GET
`works/originals` | All original works | GET, POST
`works/translations` | All translations | GET, POST

#### Originals

Prefix: `api/works/originals/`

URL | Content | Methods
----|---------|--------
`<trustee_code>` | All originals of one trustee | GET, POST
`<trustee_code>/<language_code>` | All originals of one trustee and language | GET, POST
`<trustee_code>/<language_code>/<work_code>` | Specific original work | GET, POST
`<trustee_code>/<language_code>/<work_code>/sections` | Sections of an original work | GET, POST
`<trustee_code>/<language_code>/<work_code>/sections/<id>` | Specific section of an original work | GET, PUT, PATCH
`<trustee_code>/<language_code>/<work_code>/pages/<page>` | Specific page of an original work | GET
`<author_slug>` | All originals of one author | GET, POST
`<language_code>` | All originals of one language | GET, POST

#### Translations

Prefix: `api/works/translations/`

URL | Content | Methods
----|---------|--------
`<language_code>` | All translations of one language | GET, POST
`<author_slug>` | All translations of one author | GET, POST
`<author_slug>/<language_code>` | All translations of one author and language | GET, POST
`<author_slug>/<language_code>/<work_code>` | Specific translated work (newest edition or development) | GET, POST
`<author_slug>/<language_code>/<work_code>/<edition>` | Specific edition of a translated work | GET, POST
`<author_slug>/<language_code>/<work_code>/editions` | Editions of a translated work | GET, POST
`<author_slug>/<language_code>/<work_code>/sections` | Sections of a translated work | GET, POST
`<author_slug>/<language_code>/<work_code>[/<edition>]/<section_id>` | Specific section of a translated work | GET, PUT, PATCH
`<author_slug>/<language_code>/<work_code>[/<edition>]/<section_id>/history` | History of a specific section | GET
`<author_slug>/<language_code>/<work_code>/pages` | Pages of a translated work | GET
`<author_slug>/<language_code>/<work_code>/pages/<page>` | Specific page of a translated work | GET

Note: Private works are included only if you have access rights.

### Users
