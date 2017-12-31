# Quality assurance

To guarantee a high quality in translations is a complex subject. Our aim is to provide
* high precision,
* beautiful language,
* preservation of the author’s spirit,
* language consistency,
* exactness in spelling and grammar and
* consistency in formatting.

For that purpose we provide a multi layer validation. A paragraph will be marked if there is an exception to a rule and we will provide filters to be able to update segments in question easily. All exceptions have to be solved before a work is released. Releases are public versions of a work (online, offline, printed, acoustic).


## Community

As good as everybody can contribute in the translation. A community is stronger and has a wider view than a few persons. People will share their specialist knowledge and bring in their experience.


## Permissions

Users may have many different permissions. Trustees assign them for their works according to the trust they have in the user. Users gather points for doing things well and lose points otherwise. This may be a help to judge a user. See the permission documentation for more details.


## Tracking

Every change is saved with user and time information and can be seen in the history. In this way you may restore an older version which lost quality in a later version. Users will be more careful as their names are associated with every record.


## Discussion

You can share your thoughts on a paragraph. By this people may share uncertainties and get answers or understand why something should be changed or be kept.


## Precision

### Community driven
* Rules will guide translators what to pay attention to, e.g.
    * ”should“ = “sollte“, not “soll“
    * ”many“ = “viele“, not “manche“
* 4+ authorised users will have to review every paragraph before a work gets released
* Releases are multi proof read snapshots and cannot be changed
* Authorised users have to review edits of new users before they are visible to the community
* Users might mark paragraphs as not being accurate

### Automated
* Users cannot add or delete headings or paragraphs.
* The characters of each paragraph will be numbered and compared to the translation. Incomplete paragraphs will be detected on the basis of a language specific ratio (with a tolerance) and marked.
* Scans for false friends.


## Beautiful language

* Guidelines, e.g.
    * avoid ”man“
    * avoid too long sentences
* Reviews (see prior section)
* Users might mark paragraphs as not being beautiful
* Scans for similar spelling of certain words in original and translation (there might be a better word but the translator went the easiest way and took the original word and just adjusted it to fit the language, e.g. ”example“ = “Exempel“ (bad) = “Beispiel“ (good))


## Author’s spirit

* Guidelines with quotes from the author, e.g. it is better to be too graceful than to bee to hard
* Reviews
* Paragraph marking


## Language consistency

* Translators will be asked to use
    * an exactly defined language, e.g. ”German Germany“ or “German Switzerland“
    * specific spelling rules, e.g. ”Amtliches Regelwerk in der Fassung 2011“, see
        * https://www.duden.de/sites/default/files/downloads/amtliche_Regelungen.pdf
        * http://www.rechtschreibrat.com/regeln-und-woerterverzeichnis/
    * more guidelines
* We will provide information and tutorials if possible, e.g.
    * https://www.duden.de/sprachwissen/sprachratgeber/Crashkurs-25-Schritten-zur-neuen-Rechtschreibung
    * https://www.duden.de/sprachwissen/rechtschreibregeln
* We will detect exceptions to language rules automatically where possible (see next section)
* Authorised users might mark a paragraph as not matching the language rules


## Spelling and grammar

* Mistakes will be underlined in the text.

### Software
These checks seem to be very resource intensive (RAM). We might have to rent another server for that or they have the software as a service (SaaS) we pay for. Or we do the checks seldom.

We might use one or several of those:
* https://www.languagetool.org/ (spelling, grammar and more checker, 20+ languages)
* http://www.afterthedeadline.com/ (spell, style, grammar checker, 5 languages)
* http://www.gingersoftware.com/ (grammar checker, sentence rephrase, English only but might be the best)
* https://spacy.io/ (syntactic parser)
* http://www.nltk.org/ (Natural Language Toolkit)


## Formatting

### Automated corrections

#### Block formats
Formats which apply to a text unit enclosed by line breaks cannot be altered by a user. (That is heading and paragraph formats. Examples are the well-known HTML tags `h1` and `blockquote` and their classes.)

#### Removal
* leading, trailing and double whitespaces,

#### Substitutions

Sign | substitute
-----|-----------
' | ’
' | ‘
' | ‚
' | ’
" | “
" | „
" | ”
... | …

### Checks

#### Equality
The numbers of following signs and formats have to be equal to the original. Authorised users might silence these warnings on a paragraph basis. (Language specific differences will be considered.)
* ’
* ‚
* ‘
* ”
* ”
* »
* «
* ›
* ‹
* …
* (
* )
* {
* }
* [
* ]
* –/—
* ?
* **bold**
* *italic*

#### References
The title of the reference has to be equal to the original or has to be found in the database together with the correct link. Authorised users might silence these warnings on a paragraph basis.


## Copyright protection

This is a special topic and of consequence especially for printed works, because they cannot be changed without financial loss.
* Users are informed that the whole responsibility for their content lies with them. Therefore they should be aware of the copyright and accordingly careful.
* Publishing houses are asked to hand in their translations in order to detect possible infringements of copyright. Scans will be done right before the final review. Printing houses might get a list of checked translations if they want to scan further translations.
* Only authorised users are allowed to copy text into the online editor. Copying is detected by monitoring key strokes and mouse clicks and huge changes between draft versions.

