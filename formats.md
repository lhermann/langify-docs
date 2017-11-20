# Formats

Formats for the books and articles we one day might support per one click. Others might be added.

## Import

AZW, AZW3, AZW4, CBZ, CBR, CBC, CHM, DJVU, DOCX, EPUB, FB2, HTML, HTMLZ, LIT, LRF, MOBI, ODT, PDF, PRC, PDB, PML, RB, RTF, SNB, TCR, TXT, TXTZ

Best source formats in order of decreasing preference: LIT, MOBI, AZW, EPUB, AZW3, FB2, DOCX, HTML, PRC, ODT, RTF, PDB, TXT, PDF

## Export

AZW3, EPUB, DOCX, FB2, HTMLZ, OEB, LIT, LRF, MOBI, PDB, PMLZ, RB, PDF, RTF, SNB, TCR, TXT, TXTZ, ZIP

## Internal use

We save the works internally using HTML.

Usage | Calibre | Langify
------|---------|--------
paragraph | `<p>` | `<p>`
title, headline | `<h1>` – `<h6>` | `<h1>` – `<h6>`
italic | `<i>` | `<i>`
bold | `<b>` | `<b>`
underline | `<u>` | `<u>`
subscript | `<sub>` | `<sub>`
supscript | `<sup>` | `<sup>`
thematic break | | `<hr>`
reference* | `<a>` | `<a>`

And maybe all signs in [here](https://github.com/kovidgoyal/calibre/blob/master/src/calibre/ebooks/html_entities.py).

*= includes URLs, other works, bible, pages. Maybe we could use the [data](https://www.w3schools.com/tags/tag_data.asp) tag for pages, works and bible.

Other HTML tags we might support: abbr, lists, tables, blockquote, definitions, kdb, s, var, small, cite, code, summary, ...

CSS we should support: text-align
