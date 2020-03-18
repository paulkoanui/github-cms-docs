## Setup a Source Content Repository
You can use any GitHub Repository (public or private) that has Issues that you'd like to publish to a Target Publication Repository.  

> Examples in this documentation will use `paulkoanui/source-content-repo-1` as the Source Content Repository.

**To enable publication on your repository, you will:**
- Create one or more GitHub Projects on the repository.  Issues that you wish to publish go in these Collection projects.
- Define a Publication Workflow that uses [GitHub CMS Action](https://github.com/paulkoanui/github-cms-action)

> [GitHub CMS Action](https://github.com/paulkoanui/github-cms-action) is an open source GitHub Action that executes the publication process when Issues inside of a Project change columns (state).  It can be used without downloading anything.  Think of it like a GitHub Repository Plugin.

### Create a Collection Project

1. In a GitHub Repository, go to Projects.
2. Create a Project and add state columns.  

For example, in the video below, we create a Project called "Posts" that will be used to publish Jekyll formatted blog posts.

<div class="videoWrapper"><iframe width="560" height="315" src="https://www.youtube.com/embed/D0032yM-EYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>


### Define a Publication Workflow

This is a YAML file, called `github-cms.yml`, that belongs in the Source Content Repository at `.github/workflows`.
> See the [Configuring a Workflow](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) for GitHub Actions for more info.

The [workflow](https://github.com/paulkoanui/github-cms/blob/master/.github/workflows/github-cms.yml) used by the Github CMS reference implementation (which published what you are reading now) is a good example of how to configure and use the GitHub CMS Action.

You should have the repository details for your Source, Target, and Meta repositories before you can configure the Workflow to run.  

The repository details you will need for each of the three are:
- Repository owner. e.g. In `paulkoanui/github-cms`, `paulkoanui` is the owner
- Repository name. e.g. In `paulkoanui/github-cms`, `github-cms` is the name
- Valid access token, with `repo` scope, for authentication with the repository via GitHub API.

#### Configure Source Repository Details
https://github.com/paulkoanui/github-cms/blob/7acb1946b7836efbfeea37b17946fd9cecd6a9e7/.github/workflows/github-cms.yml#L9-L12
In the example above, the access token is stored as an encrypted Secret injected by GitHub Actions.  The owner and repository names are taken from the GitHub event context that is available at run time.
> See [Using variables and secrets in a workflow](https://help.github.com/en/actions/configuring-and-managing-workflows/using-variables-and-secrets-in-a-workflow) for information about the special GITHUB_TOKEN secret.
> See [Context and expression syntax for GitHub Actions](https://help.github.com/en/actions/reference/context-and-expression-syntax-for-github-actions) for more information about the GitHub context and other objects available at run time.
