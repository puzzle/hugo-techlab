# Lab 5: Templates

In the last lab we added some content. Hugo uses template files to render content (markdown) into HTML. Template files are a bridge between the content and presentation. Hugo doesn't provide any default templates, meaning that content is not rendered by default.

The terms layout and template are used interchangeably. The directory is called `layouts`, but the layouts also contain template variables and functions.

The goal of this lab is to render our content (e.g. `content/labs/01_quicktour.md`) to HTML.

There are three types of templates: single, list, and partial. Each type takes a bit of content as input and transforms it based on the commands in the template.

In this lab we will be be focussing on the following templates:
- Homepage
- Section pages (list template)
- Regular pages (single template)

A section page is a list of regular pages in a specific section. In our example (`content/labs/01_quicktour.md`) the section is `labs` and all files inside this directory are regular pages.

## Lookup order
There are lookup rules for each page. That means that Hugo checks if specific layout exists. If it doesn't exist then Hugo searches for the next layout (in the lookup order). The first layout that exists will be used.

The lookup order for the Homepage is (first file found will be used):

- layouts/index.html
- layouts/_default/list.html

The lookup order for the labs section is:

- layouts/labs/list.html
- layouts/_default/list.html

The lookup order for a regular page (in the labs section):

- layouts/labs/single.html
- layouts_default/single.html

These lists have been shortened. To find out more about Hugo's lookup order, see the [official docs](https://gohugo.io/templates/lookup-order/)

## Basic Syntax

### Variables
Accessing variables is easy. The hard part is knowing which variables are available. In Hugo there are different variable scopes:
 - [Site variables](https://gohugo.io/variables/site/)
 - [Page variables](https://gohugo.io/variables/page/)
 - [Section variables](https://gohugo.io/variables/page/#section-variables-and-methods)
 - [Taxonomy variables](https://gohugo.io/variables/taxonomy/)

And a few more... As you may guess the site variables are global and can be accessed everywhere. Every layer below the site variables adds more specific variables, but also has access to all the more general variables.

e.g. A section template has access to the section variables, but also page and site variables.

When editing the layouts you will mostly encounter [page variables](https://gohugo.io/variables/page/). The following is a small list of the most important ones:

**.Content**

the content itself, defined below the front matter.

**.Title**

the title for this page.

**.Date**

the date associated with the page; .Date pulls from the date field in a content’s front matter.

**.Params**

contains all other values defined in the front matter (e.g. `.Params.tags`).

**.Permalink**

the link to this page

### Functions
TODO

## Exercise: list all the labs
TODO

## Exercise

Create a layout (with template variables), that renders a single lab page.

<details>
  <summary>Solution</summary>

  TODO
</details>

---

**Ende Lab 5**

<p width="100px" align="right"><a href="04_templates.md">Templates →</a></p>

[← back to the overview](../README.md)
