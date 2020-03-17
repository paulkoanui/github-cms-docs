## Glossary of Terms

- **Content management system** is defined as a system for managing web pages and/or posts.  It provides functionality that allows users to draft, publish, archive, and delete content.  It represents the source of truth for all content that it manages.
- **Content publication** is the process of synchronizing source content with some target system based on the content's publication state.
- **Source system** for all content is GitHub Issues where each issue represents one content item.
- **Target system** is a GitHub repository where published content items are rendered as Markdown files.  This repository is rendered as a website with GitHub Pages.
- **Meta system** is a GitHub repository where source/target relationships are stored as JSON files. When source content is published, metadata regarding the source/target relationship is updated.
- **Publication states** are managed through a GitHub Project that acts as a state machine.
- **Publication actions** are defined with JavaScript in Node.js and executed by GitHub Actions. 

## Publication States
Source content can be in one of four publication states:
- Staged
  - Items in this state are "staged" for a publishing action.  That means, moving from this state to Published or Archived will execute that publishing action (Publish or Archive).  Moving from Published or Archived to this state will produce no publishing action.
- Published
  - Items in this state have a metadata record that relates the source item to a target item.
- Archived
  - Items in this state have a metadata record that relates the source item to a target item.
- Unpublished
  - Items in this state are not mapped to the target system.  There is no metadata record for the source item.  If the item is currently in a Published or Archived state, it will be removed from the target system and its metadata record will also be removed.





## Publication Actions
_**TODO**_