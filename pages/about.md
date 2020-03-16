---
layout: page
title: About
permalink: /about/
weight: 3
tags: 
  []
---

# About GitHub CMS

A GitHub repository has all of the ingredients for serving as a content management system.

![image](https://user-images.githubusercontent.com/2074485/76781437-1a6ec600-6785-11ea-9849-1613d0d716b6.png)


In the scope of this project:
- **Content management system** is defined as a system for managing web pages and/or posts.  It provides functionality that allows users to draft, publish, archive, and delete content.  It represents the source of truth for all content that it manages.
- **Content publication** is the process of synchronizing source content with some target system based on the content's publication state.
- **Source system** for all content is GitHub Issues where each issue represents one content item.
- **Target system** is a GitHub repository where published content items are rendered as Markdown files.  This repository is rendered as a website with GitHub Pages.
- **Meta system** is a GitHub repository where source/target relationships are stored as JSON files. When source content is published, metadata regarding the source/target relationship is updated.
- **Publication states** are managed through a GitHub Project that acts as a state machine.
- **Publication actions** are defined with JavaScript in Node.js and executed by GitHub Actions. 

[**See to "Docs" to learn more.**](/docs/)