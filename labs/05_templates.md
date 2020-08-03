# Lab 5: Templates

In the last lab we added some content. Hugo uses template files to render content (markdown) into HTML. Template files are a bridge between the content and presentation. Hugo doesn't provide any default templates, meaning that content is not rendered by default.

There are three types of templates: single, list, and partial. Each type takes a bit of content as input and transforms it based on the commands in the template.

TODO: describe template lookup order

Layouts mainly contain HTML, but can also include variables and functions. This is called templating. All template variables and functions are accessible within `{{ }}`.

In this lab we will get to know the most important variables and functions and how to use them.

The goal is to render our content (e.g. `content/labs/01_quicktour.md`) to HTML.

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


---

**Ende Lab 5**

<p width="100px" align="right"><a href="04_templates.md">Templates →</a></p>

[← back to the overview](../README.md)
