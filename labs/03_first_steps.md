# Lab 3: First Steps

In this lab we will create a new Hugo project.

## Preparation for the labs

Please clone the git repository, to have a local copy of all necessary excercises.

```
$ cd [Git Repo Project Folder]
$ git clone https://github.com/puzzle/hugo-techlab.git
```

As a fallback the repository can be downloaded as a [zip file](https://github.com/puzzle/hugo-techlab/archive/master.zip).

## Create a New Project

**Note:** Please make sure, you are finshed with [Lab 2](02_cli.md).

The following command creates a new directory `mysite`. You can name the project however you like.
```
$ cd [Git Repo Project Folder]
$ hugo new site mysite
Congratulations! Your new Hugo site is created in /home/lbischof/git/mysite.

$ cd mysite

$ ls -l
total 28
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 archetypes
-rw-r--r-- 1 lbischof lbischof   82 Jul 30 08:46 config.toml
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 content
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 data
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 layouts
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 static
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 08:46 themes
```

The following files and directories were created:
- `archetypes/` contains templates for creating new content. Try running `hugo new labs/some-new-lab.md`.
- `config.toml` is the configuration file for Hugo.
- `content/` contains all the content in Markdown format. Explained in [Lab 04](04_content.md).
- `data/` may contain additional data files in Yaml or JSON format. See the [Hugo docs](https://gohugo.io/templates/data-templates/#the-data-folder) for more information.
- `layouts/` define how the Markdown files are converted to HTML. Explained in [Lab 05](05_templates.md)
- `static/` is copied, without any changes. A file `static/example.jpg` is later accessible at `http://localhost:1313/example.jpg`.
- `themes/` is described below.

Now run `hugo` to build the site. The generated content is in `./public`:
```
$ ls -l public
total 16
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:10 categories
-rw-r--r-- 1 lbischof lbischof  467 Jul 30 09:10 index.xml
-rw-r--r-- 1 lbischof lbischof  355 Jul 30 09:10 sitemap.xml
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:10 tags
```
As we can see there is no `index.html` file.

The following files were created:
 - Two directories `categories` and `tags`. These are the default [taxenomies](https://gohugo.io/content-management/taxonomies/) that group content together (e.g. all the posts in a specific category or tag)
 - An RSS feed `index.xml` and the sitemap `sitemap.xml`

## Create a new theme

In the last step you may have noticed that Hugo does not create any HTML files. The reason for this, is that Hugo does not have a default theme. You can either create your own or download one from https://themes.gohugo.io.

Since the goal of this lab is to show you how themes work, we will create our own theme. This theme will not be pretty, but rather functional.

The following command creates a skeleton theme:
```
$ cd mysite
$ hugo new theme mytheme
Creating theme at /home/lbischof/git/mysite/themes/mytheme

$ ls -l themes/mytheme
total 20
-rw-r--r-- 1 lbischof lbischof 1081 Jul 30 09:02 LICENSE
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:02 archetypes
drwxr-xr-x 4 lbischof lbischof 4096 Jul 30 09:02 layouts
drwxr-xr-x 4 lbischof lbischof 4096 Jul 30 09:02 static
-rw-r--r-- 1 lbischof lbischof  435 Jul 30 09:02 theme.toml
```
You might notice, that these directories are the same as above (main directory). This is not a coincidence. The same directories can be used at both places. If there are conflicts (same file names), the theme file is overwritten:

<pre>
.
├── <b>layouts</b>
│   └── labs
│       └── <b>single.html</b>
└── themes
    └── mytheme
        └── <b>layouts</b>
            └── labs
                ├── list.html
                └── <b>single.html</b>
</pre>
In the above example, we overwrite `single.html` outside of the theme. This can be really useful, if we downloaded the theme from Github.

Note that the skeleton's template files are empty. Don't worry, we'll be changing that shortly.
```
$ find themes/mytheme -name '*.html' | xargs ls -l
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/404.html
-rw-r--r-- 1 lbischof lbischof 250 Jul 30 09:02 themes/mytheme/layouts/_default/baseof.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/_default/list.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/_default/single.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/index.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/partials/footer.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/partials/head.html
-rw-r--r-- 1 lbischof lbischof   0 Jul 30 09:02 themes/mytheme/layouts/partials/header.html
```

## Update the Configuration File to Use the Theme

Now that we've got a theme to work with, it's a good idea to add the theme name to the configuration file.

Now specify the theme name in the configuration `config.toml`:
```
theme = "mytheme"
```

Now generate the site again:
```
$ hugo
```
Did you notice that the output is different? The warning messages regarding the missing layouts have disappeared.

```
$ ls -l public
total 24
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:10 categories
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:02 css
-rw-r--r-- 1 lbischof lbischof  467 Jul 30 09:15 index.xml
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:02 js
-rw-r--r-- 1 lbischof lbischof  355 Jul 30 09:15 sitemap.xml
drwxr-xr-x 2 lbischof lbischof 4096 Jul 30 09:10 tags
```
As you can see there are still no HTML files. The `css` and `js` directories were created because these exist in `themes/mytheme/static`. Everything in the `static` directory is copied directly into `./public`. This confirms that our theme is working correctly.

## Layouts

Hugo uses template files to render content (markdown) into HTML. Template files are a bridge between the content and presentation.

Without templates we would have to copy and paste the header and footer to each page. With templates we define the header and footer once and Hugo automatically includes it in every page. Templates are basically what made static sites great again.

Hugo doesn't provide any default templates, meaning that content is not rendered by default.

In lab 5 we will create templates, but first we will learn how to add content.

---

**Ende Lab 3**

<p width="100px" align="right"><a href="04_content.md">Content →</a></p>

[← back to the overview](../README.md)
