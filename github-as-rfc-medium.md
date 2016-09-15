# GitHub as an RFC medium

## Problem
Common approach at many organization for RFCs is to use
[Google Docs](https://www.google.com/intl/en/docs/about/).
While it has some support for revision tracking, commenting, and modification
suggestions, GDocs fails at the core RPC process:
 1. Gathering meaningful feedback
 2. Allowing non-destructive, isolated contributions
 3. Atomic revisions

### Meaningful feedback
The feedback in Google Docs is done via comments, which are relegated to the
side of the main document as a narrow column of text. It's sufficient for
small, one-off suggestions, but any exchange of non-trivial ideas results in a
multi-page 'ribbon' of text. Such format doesn't scale for any meaningful
discussion and thus ultimately discourages it.

### Non-destructive, isolated contributions
With GDocs there are 3 work modes:
 1. Editing (destructive) - an old text is immediately replaced by a new text
    without a review / approval process.

 2. Suggesting (non-destructive, non-isolated) - both original and suggested
    text is present in the document until the suggestion is either accepted or
    rejected. Suggestions are dealt on one-by-one basis (there is no grouping
    mechanism to help the subsequent readers to follow related changes)

 3. Viewing (no changes) - a document is displayed in a version with all
    suggestions removed. I'm not aware of a mode / view setting to allow viewing
    of a version as it would look like with all or a group of suggestions
    accepted.

Additionally, GDocs is a synchronous tool, where everybody works on the same
document (no isolation). As such it effectively prevents more than person
suggesting changes to the same section of the document at the same time.

### Atomic revisions
With GDocs every change automatically creates a new revision. If multiple
people contribute at the same time, their revisions are interspersed and lack
logical grouping. To cut down on the noise some revisions are automatically
bundled based on time proximity - this view is available as 'show less detailed
revisions'. This is a band-aid that does not provide atomicity of changes.

## Proposal
GitHub with its rendering of Markdown format (incl. images and tables)
creates an appealing alternative since it addresses the aforementioned
shortcomings of GDocs. The description below is brief since it's a tool
well-known to us.

### Meaningful feedback
Comments are given the same priority (width-wise) and the same rich-text
formatting as the main text. Thus not discouraging longer exchanges of ideas.
With GitHub new features, a reviewer can choose between giving individual
comments or grouping the feedback into a one (atomic) review. With the latter,
a reviewer can choose between a general feedback, approval, or request for
changes before an RFC can go into effect (i.e., can be merged into master).

### Non-destructive, isolated contributions
Multiple reviewers can submit any number of larger contributions (as opposed to
just commenting). Group them logically as a commit and further group commits as
a PR. An RFC can be read in its original form as submitted by original authors
and also with the proposed changes by each reviewer, but without the visual
noise of crossed-out text.

### Atomic revisions
All changes are logically grouped in revisions (commits) by their authors and
are atomically applied to an RFC. All revisions have a commit message to give
the reader context for the changes. Merging to master means the RFC or its
subsequent changes are in effect.

## Pros
- Since Git is designed for tracking revisions it handles it much better than
GDocs (a web-based word processor).
- Github adds commenting, proposing bigger changes, and review process that is
  significantly better than bolted-on comments, suggestion mode, and
  'revisions' of GDocs

## Cons
- RFC participants need a Github account - this shouldn't be an issue for any
  member of tech org
- Drawings cannot be edited in-place. However, GDocs only allows this in
  (destructive) direct editing mode. And once a drawing is saved the previous
  version is lost.

## Conclusion
![developers by balmer](http://i.makeagif.com/media/11-18-2015/Q9zI1Y.gif)
