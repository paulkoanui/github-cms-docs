# Content Management

## Stage Content
Staged content are GitHub Issues organized in the "Staging" column of a GitHub Project.  Items in this state are waiting to be published or archived.

From the Source Content Repository:
- Go to the GitHub Project where you wish to stage content
- Click "Add Cards" to bring up a list of all Issues
- Drag an Issue card into the "Staging" column
- GitHub CMS Action doesn't perform any action when an item is moved into Staging.  

> "Staging" is simply an organizational state that says, "This item belongs in this collection but is not ready to be published or archived in its current form."

## Publish Content
Published content are GitHub Issues organized in the "Published" column of a GitHub Project.  Items in this state are published to the Target Publication Repository.

From the Source Content Repository:
- Go to the GitHub Project where you wish to publish content
- Drag an Issue card from "Staging" or "Archived" columns into the "Published" column
- GitHub CMS Action responds to the state change and publishes the content

## Archive Content
Archived content are GitHub Issues organized in the "Archived" column of a GitHub Project.  Items in this state are archived to the Target Publication Repository.

> The publication workflow, `github-cms.yml`, specifies the `TARGET_ARCHIVE_PATH` environment variable.  The default value is `_archive`.  So, if a published item exists at `_pages/my-content-page.md`, the archived path is, `_archive/_pages/my-content-page.md`.

From the Source Content Repository:
- Go to the GitHub Project where you wish to archive content
- Drag an Issue card from "Staging" or "Published" columns into the "Archived" column
- GitHub CMS Action responds to the state change and archives the content

## Unpublish Content
In order to unpublish content, you must remove it from the GitHub Project that manages its publication state.

From the Source Content Repository:
- Go to the GitHub Project where you wish to unpublish content
- Open the context menu for the item you wish to unpublish and choose "Remove from Project"
- GitHub CMS Action responds to the state change and unpublishes the content