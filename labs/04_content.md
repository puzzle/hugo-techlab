# Lab 4: Content

In the last lab we created a new site and theme. We learned about layouts and added a simple `index.html` page.

Content is stored in text files that contain two sections. The first section is the "front matter," which is the meta-information on the content. The second section contains Markdown that will be converted to HTML.

The following is an example file. The data enclosed in `---` is front matter. Everything below the front matter is the markdown content.
```
---
title: This is an example
draft: true
date: 2020-07-01
---
This is markdown content
```

## Front Matter

The front matter is information about the content. It can be formatted in YAML, TOML, or JSON. We will be using YAML in these labs. For more information about other formats visit the [Hugo documentation](https://gohugo.io/content-management/front-matter/).

The information in the front matter is passed into the template before the content is rendered into HTML.

### Predefined Variables
There are predefined variables that can be used in the front matter and sometimes change the behaviour of Hugo. The most important ones are listed below, for a full list visit the [Hugo documentation](https://gohugo.io/content-management/front-matter/#front-matter-variables).

**date**<br>
the datetime assigned to this page.

**draft**<br>
if `true`, the content will not be rendered unless the `--buildDrafts` flag is passed to the hugo command.

**title**<br>
the title for the content.

**weight**<br>
used for ordering your content in lists. Lower weight gets higher precedence. So content with lower weight will come first.

### User-Defined
You can add fields to your front matter arbitrarily to meet your needs. These user-defined key-values are placed into a single `.Params` variable for use in your templates.

## Markdown
Content is written in Markdown which makes it easier to create the content. Hugo runs the content through a Markdown engine to create the HTML which will be written to the output file.

## Exercise
Create a new Markdown file (`.md`) in `./content/labs/` and add some front matter. You can use the Markdown files from this repository.

<details>
  <summary>Solution</summary>

  ```
  mkdir content/labs
  curl -o content/labs/01_quicktour.md https://raw.githubusercontent.com/puzzle/hugo-techlab/master/labs/01_quicktour.md
  ```
  Now add the following front matter at the top of `content/labs/01_quicktour.md`:
  ```
  ---
  title: 1. Quicktour
  ---
  ```
  If you want you can also add additional content.
</details>

You will notice that the content is not rendered by Hugo. In the next lab we will create a template that renders the Markdown into HTML.

<details>
  <summary>Howto: check if content is rendered</summary>

  Hugo does not delete old files from `./public`. If you want a clean build, then delete it first.
  ```
  rm -rf public
  hugo
  ls -l public/labs
  ```
  By default every section has an RSS output (see `index.xml`). But the HTML file is not generated, because there is no matching template in `./layouts`.
</details>

---

**Ende Lab 4**

<p width="100px" align="right"><a href="05_templates.md">Templates →</a></p>

[← back to the overview](../README.md)
