# Architecture
There are four pieces that enable publishing:
1. Publication process to execute publishing actions in response to content state changes
2. Content "Source of Truth"
3. Location to store published content
4. Publication metadata

> The architecture presented here is separated by functional role within the system (and, therefore, into separate repositories).  Separate repositories are not a requirement and GitHub CMS can be completely self contained in a single repository.

## Publication Process
The GitHub CMS Action represents the process that executes publication actions and manages publication state.  This action is used by a Source Content Repository.

## Source Content Repository
The GitHub Issues in this repository represent the "Source of Truth" for all content that is published by GitHub CMS Action.  A GitHub Issue and content item are used interchangeably.  They are the same from our perspective.

GitHub Projects in this repository are used to organize Issues into "Collections".  These projects also represent state machines used to move Issues between Staging, Published, Unpublished, and Archived states.  State changes are observed and reacted to by GitHub CMS Action. 

## Target Publication Repository
This GitHub Repository hosts all content published from the Source Content Repository.  GitHub CMS is configured to generate Markdown formatted text files containing Jekyll front-matter.  This allows instant support for hosting published content with GitHub Pages.

## Metadata Repository
This GitHub Repository stores the following information content items:
- Issue Number - of the content item in the Source Content Repository.
- Publication State - whether `published`, `archived`.
- Target Content Location - the path to the file where the target content item resides.
- Last Updated - the timestamp of the last publication change for the content item.