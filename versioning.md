# Versioning

## Example

```
Source
   └────────┬────────────┐
          Edition 1    Edition 2
            │            └────────────┬─────────────┐
Translation ├────────────┐            │             │
   └────────┬────────────┬────────────┬─────────────┐
          Release 1    Release 2    Release 3     Development
            │            │            │             ├────────┐
          History      History      History       History  Drafts
            └────────────┴────────────┴─────────────┤
                                                  History
```

## Terms

**Source**: Material to be translated.

**Translation**: Translation of a work (book/article).

**Edition**: A particular form or version of a published text.

**Release**: A translation state ready for production. This state gets published in several formats (epub, mobi, pdf, etc.) and at this point the printing houses take on.

**History**: Shows past contributions (create, edit, delelte) by users including date and changes.

**Draft**: Private place where to store the translation until your entry is ready. Your changes are saved every 5 s automatically. You can view every saved state for one month. The draft becomes final/public after 5 min after leaving the paragraph (or by a reviewer if you don't have the translator privilege).

## Concepts (database level)

This section handles the representation of editions, releases and histories in the database. The objects are [slowly changing dimensions](https://en.wikipedia.org/wiki/Slowly_changing_dimension). Types in question are type 2 and 4.

### Type 2

Add a new row. App: [CleanerVersion](http://cleanerversion.readthedocs.io/)

#### Pros

- History remains.
- Historical relationships point to the correct historical object (?).
- Better access to historical objects (?).

#### Cons

- Heavier queries on lookups other than ID.
- Many changes in the code.
- You have to care for a new version yourself (in the code).
- You cannot amend releases, only the latest (development) version.
- Unknown component to me.

#### 1. Release as time stamp

There is one object over the whole life of a translation. The history grows as there come revisions and releases. Releases are determined by a time stamp.

### Type 4

Add a history table. App: [Django reversion](https://django-reversion.readthedocs.io/)

#### Pros

- Stores meta-information by default (user, time stamp, comment).
- Queries are slenderer.

#### Cons

- Heavier queries on historical objects (?).
- Historical relations might point to the current object (depends on implementation).

#### 2. Release as time stamp

There is one object over the whole life of a translation. The history grows as there come revisions and releases. Releases are determined by a time stamp.

##### Pros

- History remains.
- Less data.

##### Cons

- You cannot amend releases, only the latest development version.

#### 3. Object per release

There is one seperate object for every release. As a result each release has it's own history.

##### Pros

- You can amend releases (they are independent).

##### Cons

- The development version after a release has an empty history. Possible solution: copy the whole history.

#### 4. Release as snapshot (copy)

There is one object over the whole life of a translation. The history grows as there come revisions and releases. Releasing means that you copy the content into another object which will be used to jsut store this state.

##### Pros

- History remains.
- Quick access to releases.

##### Cons

- You cannot (really) amend releases, only the latest development version.
- More data.

### Conclusion

I'll use type 4 and implement "release as snapshot" maybe in combination with "release as time stamp" depending on the public API: If the API includes the release I'll keep all release copies. Otherwise I keep the newest only.

## Notes

- New editions of source material are checked against the development version only. However, you can make a manual check where a time stamp will be used.
- The work gets protected during amendments right before a new release should be completed. You may revise it during that time but your updates stay in the draft. However, persons who are in charge of the amendments may consider your revisions.

## Issues

- If we have an update in a source edition we still (dispite versioning) have to implement a marker that the section updated needs a review in the translation to be removed after the review.

