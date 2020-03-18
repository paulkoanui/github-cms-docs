## Setup a Source Content Repository
You can use any GitHub Repository (public or private) that has Issues that you'd like to publish to a Target Publication Repository.  

**To enable publication on your repository, you will:**
- Create one or more GitHub Projects on the repository.  Issues that you wish to publish go in these Collection projects.
- Define a Publication Workflow that uses [GitHub CMS Action](https://github.com/paulkoanui/github-cms-action)

> [GitHub CMS Action](https://github.com/paulkoanui/github-cms-action) is an open source GitHub Action that executes the publication process when Issues inside of a Project change columns (state).  It can be used without downloading anything.  Think of it like a GitHub Repository Plugin.

### Create a Collection Project
In a GitHub Repository, go to Projects
![image](https://user-images.githubusercontent.com/2074485/76915027-58a5db80-6892-11ea-9298-cd11364363af.png)

Create a Project and add state columns.  For example, in the video below, we create a Project called "Posts" that will be used to publish Jekyll formatted blog posts.

<div class="videoWrapper"><iframe width="560" height="315" src="https://www.youtube.com/embed/D0032yM-EYw" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>


### Define a Publication Workflow
_**TODO**_
