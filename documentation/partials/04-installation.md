# Installation
This guide will show you how to **setup GitHub CMS across three separate repositories** aligning to the following roles:
- Source Content Repository
- Target Publication Repository
- Meta Repository

You must have an access token with the `repo` scope on the three repositories above.  The easiest way to do this is to make sure all of the repositories are in your account and create a Personal Access Token with the `repo` scope.

> See [Creating a personal access token for the command line](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line) for more information.

Although separate repositories makes the components of the system very clear and flexible, it is not a requirement that you create one repository per role.  

**GitHub CMS can be setup in a single repository, if you wish**.  Simply use the same repository as you follow the setup instructions below.

## Setup the Meta Repository
You can use any GitHub Repository (public or private) that you have `repo` access to. For this example, a repository was created at `paulkoanui/meta-repo-1`.

META_OWNER | META_REPO
-- | --
paulkoanui | meta-repo-1

> _(in a future step, you will configure the publication workflow to use the above values)_

## Setup the Target Publication Repository
You can use any GitHub Repository (public or private) that you have `repo` access to. For this example, a repository was created at `paulkoanui/target-content-repo-1`.

TARGET_OWNER | TARGET_REPO
-- | --
paulkoanui | target-content-repo-1

> _(in a future step, you will configure the publication workflow to use the above values)_

## Setup the Source Content Repository
You can use any GitHub Repository (public or private) that you have `repo` access to and that has Issues you wish to publish to a Target Publication Repository.  For this example, a repository was created at `paulkoanui/source-content-repo-1`.

SRC_OWNER | SRC_REPO
-- | --
paulkoanui | source-content-repo-1

> _(in a future step, you will configure the publication workflow to use the above values)_

## Setup GitHub CMS Publication

To complete installation and setup of publication capabilities on the Source Content Repository,
- Create a GitHub Project on the repository.  It will be referred to as a Collection Project.
  - For example, `paulkoanui/source-content-repo-1` has a project called "Posts".  
  - Issues to be published go in this project.
- Define a Publication Workflow that uses GitHub CMS Action

> [GitHub CMS Action](https://github.com/paulkoanui/github-cms-action) is an open source GitHub Action that executes the publication process when Issues inside of a Project change columns (state).  It can be used without downloading anything.  Think of it like a GitHub Repository Plugin.

### Create a Collection Project

1. Go to Projects.
2. Create a Project and add state columns.  

For example, in the video below, we create a Project called "Posts" that will be used to publish Jekyll formatted blog posts.

<div class="videoWrapper"><iframe width="560" height="315" src="https://www.youtube.com/embed/D0032yM-EYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>


### Define the Publication Workflow

This is a YAML file, called `github-cms.yml`.  It defines the publication process and how it operates.  Once customized, this file will be placed in `.github/workflows` in the Source Content Repository.

> See the [Configuring a Workflow](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) for GitHub Actions for more info.

#### Copy [`github-cms.template.yml`](https://github.com/paulkoanui/github-cms-action/blob/master/workflows/github-cms.template.yml)

#### Configure Repository Details

In the `env` section of the workflow file, customize these values.  Other values that you don't have to change have been omitted for brevity.

```yaml
  # This is the source system repository
  SRC_AUTH: ***
  SRC_OWNER: paulkoanui
  SRC_REPO: source-content-repo-1
  # This is the target system repository
  TARGET_AUTH: ***
  TARGET_OWNER: paulkoanui
  TARGET_REPO: target-content-repo-1
  # This is the metadata repository
  META_AUTH: ***
  META_OWNER: paulkoanui
  META_REPO: meta-repo-1
```

#### Setup to Observe Changes in the "Posts" Project

The "Posts" Project contains three state columns "Staging", "Published", "Archived".  GitHub CMS Action observes when Issues move to the "Published" or "Archived" columns.
```yaml
  # Collections and actions mapped to project columns
  POSTS_PUBLISH_COLUMN: 8363572
  POSTS_ARCHIVE_COLUMN: 8363575
```
You can get the project column ID by choosing "Copy Column Link"
![image](https://user-images.githubusercontent.com/2074485/76920415-d1f8fa80-68a1-11ea-95be-99d34723c534.png)

### Enable the Publication Workflow

To enable all of the GitHub CMS publication features, push `github-cms.yml` to the Source Content Repository at `.github/workflows/github-cms.yml`.

### Try It Out: Publish a Post

> With `.github/workflows/github-cms.yml` in place, content publication with GitHub CMS can begin!

- Create an Issue in the Source Content Repository with a title and body.  
  - Need boilerplate content? Maybe some [Lorem Markdownum](https://jaspervdj.be/lorem-markdownum/)?
- Add the Issue to the "Posts" Project.  If "_awaiting triage_", move to Staging
- Move the Issue from the Staging column to the Published column.
- Wait a few seconds (or view the publication progress from the Actions tab)
- Go to the Target Publication Repository and observe the Issue has been published as a Jekyll formatted blog post in the `_posts` folder.