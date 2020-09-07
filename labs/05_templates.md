# Lab 5: Templates

In the last lab we added some content. Hugo uses template files to render content (markdown) into HTML. Template files are a bridge between the content and presentation. Hugo doesn't provide any default templates, meaning that content is not rendered by default.

Without templates we would have to copy and paste the header and footer to each page. With templates we define the header and footer once and Hugo automatically includes it in every page. Templates are basically what made static sites great again.

The terms layout and template are used interchangeably. The directory is called `layouts`, but the layouts also contain template variables and functions.

The goal of this lab is to render our content (e.g. `content/labs/01_quicktour.md`) to HTML.

There are three types of templates: single, list, and partial. Each type takes a bit of content as input and transforms it based on the commands in the template.

There are different types of pages:
- Homepage
- Section pages (list template)
- Regular pages (single template)
- Taxonomy pages (tags, categories. also list template)
- Term pages (a single tag. single template)

A section page is a list of regular pages in a specific section. In our example (`content/labs/01_quicktour.md`) the section is `labs` and all files inside this directory are regular pages.

## Lookup order
There are lookup rules for each page type. That means that Hugo checks if a specific layout exists. If it doesn't exist then Hugo searches for the next layout (in the lookup order). The first layout that exists will be used.

The lookup order for the Homepage is (first file found will be used):

- layouts/index.html
- layouts/_default/list.html

The lookup order for the labs section is:

- layouts/labs/list.html
- layouts/_default/list.html

The lookup order for a regular page (in the labs section):

- layouts/labs/single.html
- layouts/_default/single.html

These lists have been shortened. To find out more about Hugo's lookup order, see the [official docs](https://gohugo.io/templates/lookup-order/)

## Basic Syntax

### Variables

Accessing variables is easy: `{{ .Variable }}`. The hard part is knowing which variables are available. In Hugo there are different variable scopes:
 - [Site variables](https://gohugo.io/variables/site/)
 - [Page variables](https://gohugo.io/variables/page/)
 - [Section variables](https://gohugo.io/variables/page/#section-variables-and-methods)
 - [Taxonomy variables](https://gohugo.io/variables/taxonomy/)

And a few more... As you may guess the site variables are global and can be accessed everywhere. Every layer below the site variables adds more specific variables, but also has access to all the more general variables.

e.g. A section template has access to the section variables, but also page and site variables.

Some functions also create there own scope (e.g. using `range` to loop over pages allows you to access the relevant pages variables)

For developers it is probably easiest to think of the leading `.` equivalent to `this` in programing languages.

When editing the layouts you will mostly encounter [page variables](https://gohugo.io/variables/page/). The following is a small list of the most important ones:

**.Content**<br>
the content itself, defined below the front matter.

**.Title**<br>
the title for this page.

**.Date**<br>
the date associated with the page; .Date pulls from the date field in a content’s front matter.

**.Params**<br>
contains all other values defined in the front matter (e.g. `.Params.tags`).

**.Permalink**<br>
the link to this page

### Functions

Functions allow more complex behaviour. It is possible to conditionally render content or loop over pages. There are functions to uppercase a variable or check if a file exists. See the [Hugo docs](https://gohugo.io/functions) for a full list.

Functions have the basic syntax:

```
{{ function argument1 argument2 }}
```
This is a bit different than other languages where it would be `function(argument1, argument2)`.

An example with `eq`:
```
{{ eq 1 2 }}
<!-- prints false -->
```

**range**<br>
Loops over a list of items.

See https://gohugo.io/templates/introduction/#iteration for examples.

**eq**<br>
Compares two numbers and returns true if they are equal.

See https://gohugo.io/templates/introduction/#conditionals for some examples with `if`.

**ne**<br>
The inverse of `eq`.

**isset**<br>
Checks if the variable is defined.

**where**<br>
Filters a list of items based on a value.

See https://gohugo.io/functions/where/ for more information.

## Exercise: list all the labs
We would like to list all the labs on the homepage. For this we can use the `.Site.RegularPages` variable, that contains a list of all the pages. Edit `themes/mytheme/layouts/index.html` so it looks like this:
```
<h1>homepage</h1>

{{ range .Site.RegularPages }}
  <h2>
    <a href="{{ .Permalink }}">{{ .Title }}</a>
  </h2>
{{ end }}
```
Everything surrounded by `{{ }}` is interpreted by Hugo as a template. We use the `range` function to loop over all pages. Inside the `range` block we have access to the page variables of the current page.

## Exercise

Create a layout (with template variables), that renders a single lab page.

<details>
  <summary>Tip 1</summary>

  Since the page is in `./content/labs` it belongs to the `labs` section.
</details>

<details>
  <summary>Tip 2</summary>

  Layouts in `./themes/mytheme/layouts/labs/` apply to the `labs` section. You can also use `./themes/mytheme/layouts/_default/`, because it is used as a default for all sections.
</details>

<details>
  <summary>Tip 3</summary>

  Since we want to render a single page, we can use `single.html`.
</details>


<details>
  <summary>Solution</summary>

  Add the following content in `./themes/mytheme/layouts/_default/single.html`:
  ```
  <h1>{{ .Title }}</h1>
  {{ .Content }}
  ```
</details>

You can test your solution by running `hugo serve` and clicking a link on the homepage. You should see the content of the page.

<details>
  <summary>Alternative test method</summary>

  ```
  $ rm -rf public
  $ hugo
  $ ls -l public/labs
  total 12
  drwxr-xr-x 2 lbischof lbischof 4096 Aug  4 12:52 01_quicktour
  -rw-r--r-- 1 lbischof lbischof    5 Aug  4 12:52 index.html
  -rw-r--r-- 1 lbischof lbischof 1104 Aug  4 12:52 index.xml
  ```
  We see that a new directory was created (`01_quicktour`). This directory contains an `index.html` file. This is done so that URLs are pretty (without `.html` suffix).
</details>

## Conclusion

We have now created a basic website. The homepage contains a list of clickable pages. However if you view the source of the page, it doesn't contain the neccesary HTML boilerplate. (`<html><head></head><body></body></html>`)

[view-source:http://localhost:1313/](view-source:http://localhost:1313/)

In the next lab we will learn about template blocks and create a base layout that surrounds all layouts.

---

**Ende Lab 5**

<p width="100px" align="right"><a href="06_template_blocks.md">Template Blocks →</a></p>

[← back to the overview](../README.md)
