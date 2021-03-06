# Langify REST API

Documentation of URLs and their allowed methods. For the JSON objects see API OPTIONS directly.

There are options to filter and order JSON objects not mentioned here. See `OPTIONS` for details. The methods `HEAD` and `OPTIONS` are not listed here.

Under development. Please use the URLs provided in the JSON!

The interactive API can be accessed at http://127.0.0.1:8000/api/docs/ and
might replace this whole document in the future. 
(The development server should be running.)

## Private

This API is for use between front- and backend.

**Note:** Please let me know if you need the information of several JSON objects on one page frequently. We will combine them in order to reduce queries.

### Works

Prefix: `/api/`

URL | Content | Methods
----|---------|--------
`translations/` | List of translated works | GET, POST
`translations/switched-segments/` | Note about switching segments | POST
`translations/<id>/` | Specific translated work | GET, PUT, PATCH, DELETE
`translations/<id>/releases/` | List of releases | ~GET~
`translations/<id>/releases/<no>/` | Specific release | ~GET~
`translations/<id>/releases/<no>/segments/` | Segments of a release | ~GET~
`translations/<id>/segments/` | Segments of a work, including originals and drafts | GET
`translations/<id>/segments/?last_modified__gt[e]=<datetime>` | *datetime* as [ISO 8601](https://www.w3.org/TR/NOTE-datetime), e.g. `2017-12-20T12:00:00.321Z`, `+` = `%2B`! | GET
`translations/<id>/segments/<position>/` | Specific section, including original and draft | GET, ~PUT~, ~PATCH~, DELETE
`translations/<id>/segments/<position>/history/` | List of events | GET
`translations/<id>/segments/<position>/drafts/` | List of draft snapshots | GET, POST

#### JSON objects

Generally see interactive or browsable API.

##### Switching segments
```js
{
  "priorSegmentId": <id>[,
  "currentSegmentId": <id>]
}
```

### Users

Prefix: `/api/`

URL | Content | Methods
----|---------|--------
`users/<id>/` | Specific user | GET, PUT, PATCH, DELETE

### Other

Prefix: `/api/`

URL | Content
----|--------
`authors/` |
`licences/` |
`references/` |
`users/` |
`trustees/` |

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
`<trustee_code>/<language_code>/<work_code>/segments` | Segments of an original work | GET, POST
`<trustee_code>/<language_code>/<work_code>/segments/<id>` | Specific section of an original work | GET, PUT, PATCH
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
`<author_slug>/<language_code>/<work_code>/segments` | Segments of a translated work | GET, POST
`<author_slug>/<language_code>/<work_code>[/<edition>]/<segment_id>` | Specific section of a translated work | GET, PUT, PATCH
`<author_slug>/<language_code>/<work_code>[/<edition>]/<segment_id>/history` | History of a specific section | GET
`<author_slug>/<language_code>/<work_code>/pages` | Pages of a translated work | GET
`<author_slug>/<language_code>/<work_code>/pages/<page>` | Specific page of a translated work | GET

Note: Private works are included only if you have access rights.

