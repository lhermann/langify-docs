# Langify REST API

Documentation of URLs and their allowed methods. For the JSON objects see API OPTIONS directly.

All URLs are prefixed with `api/` (omitted below). `HEAD` and `OPTIONS` are not listed here.

Under development. Please use the URLs provided in the JSON!

## Works

URL | Content | Methods
----|---------|--------
`works` | All works | GET
`works/originals` | All original works | GET, POST
`works/originals/<trustee_code>` | All originals of one trustee | GET, POST
`works/originals/<trustee_code>/<language_code>` | All originals of one trustee and language | GET, POST
`works/originals/<trustee_code>/<language_code>/<work_code>` | Specific original work | GET, POST
`works/originals/<trustee_code>/<language_code>/<work_code>/sections` | Sections of an original work | GET, POST
`works/originals/<trustee_code>/<language_code>/<work_code>/sections/<id>` | Specific section of an original work | GET, PUT, PATCH
`works/originals/<trustee_code>/<language_code>/<work_code>/pages/<page>` | Specific page of an original work | GET
`works/originals/<author_slug>` | All originals of one author | GET, POST
`works/originals/<language_code>` | All originals of one language | GET, POST
`works/translations` | All translations | GET, POST
`works/translations/<language_code>` | All translations of one language | GET, POST
`works/translations/<author_slug>` | All translations of one author | GET, POST
`works/translations/<author_slug>/<language_code>` | All translations of one author and language | GET, POST
`works/translations/<author_slug>/<language_code>/<work_code>` | Specific translated work (newest edition or development) | GET, POST
`works/translations/<author_slug>/<language_code>/<work_code>/<edition>` | Specific edition of a translated work | GET, POST
`works/translations/<author_slug>/<language_code>/<work_code>/editions` | Editions of a translated work | GET, POST
`works/translations/<author_slug>/<language_code>/<work_code>/sections` | Sections of a translated work | GET, POST
`works/translations/<author_slug>/<language_code>/<work_code>[/<edition>]/<section_id>` | Specific section of a translated work | GET, PUT, PATCH
`works/translations/<author_slug>/<language_code>/<work_code>[/<edition>]/<section_id>/history` | History of a specific section | GET
`works/translations/<author_slug>/<language_code>/<work_code>/pages` | Pages of a translated work | GET
`works/translations/<author_slug>/<language_code>/<work_code>/pages/<page>` | Specific page of a translated work | GET

Notes: Private works are included only if you have access rights.

## Users
