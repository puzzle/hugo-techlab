# Lab 1: Quicktour Hugo

In this lab we will introduce the core concepts of Hugo.

## What is Hugo?

Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.

Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike systems that dynamically build a page with each visitor request, Hugo builds pages when you create or update your content. Since websites are viewed far more often than they are edited, Hugo is designed to provide an optimal viewing experience for your website’s end users and an ideal writing experience for website authors.

## The Benefits of Static Site Generators
Improved performance, security and ease of use are just a few of the reasons static site generators are so appealing. See [this blog post](https://davidwalsh.name/introduction-static-site-generators) for more detailed information.

### Speed
Web servers are really good at delivering static pages quickly, and the entire site consists of static HTML files that are sitting on the server, waiting to be served, so a request is served back to the user pretty much instantly. There are no database queries to run, no templating and no processing whatsoever on every request.

### Version control for content
Since the content is stored in flat files, it is possible to version control the content with Git.

### Security
Platforms like WordPress are used by millions of people around the world, meaning they're common targets for hackers and malicious attacks — no way around it. Wherever there's user input/authentication or multiple processes running code on every request, there's a potential security hole to exploit. To be on top of the situation, site administrators need to keep patching their systems with security updates, constantly playing cat and mouse with attackers, a routine that may be overlooked by less experienced users.

Static sites keep it simple, since there's not much to mess up when there's only a web server serving plain HTML pages.

### Less hassle with the server
Installing and maintaining the infrastructure required to run a dynamic site can be quite challenging, especially when multiple servers are involved or when something needs to be migrated. There's packages, libraries, modules and frameworks with different versions and dependencies, there's different web servers and database engines in different operating systems.

Sure, a static site generator is a software package with its dependencies as well, but that's only relevant at build time, when the site is generated. Ultimately, the end result is a collection of HTML files that can be served anywhere, scaled and migrated as needed regardless of the server-side technologies.


## Features
Hugo boasts blistering speed, robust content management, and a powerful templating language making it a great fit for all kinds of static websites.

See the [Hugo website](https://gohugo.io/about/features/) for a full list of features.

---

**End of lab 1**

<p width="100px" align="right"><a href="02_cli.md">Install the Hugo CLI →</a></p>

[← back to the overview](../README.md)
