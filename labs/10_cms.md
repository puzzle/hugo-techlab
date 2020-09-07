# Lab 10: Netlify CMS


## Setup Github authentication

Use [these instructions](https://docs.netlify.com/visitor-access/oauth-provider-tokens/#setup-and-settings) and create an Oauth Application on Github. This will be used later so that Netlify CMS can push content updates to your repository.

## Install the CMS
Now we need to add the CMS to our website.

For this we need to create a new directory and add two files. You can either directly use the `static` directory or `themes/mytheme/static` (it doesn't matter).
```
mkdir themes/mytheme/static/admin
```
and add the following content in `static/admin/index.html`:
```
<!doctype html>
<html>
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Content Manager</title>
</head>
<body>
  <!-- Include the script that builds the page and powers Netlify CMS -->
  <script src="https://unpkg.com/netlify-cms@^2.0.0/dist/netlify-cms.js"></script>
</body>
</html>
```
To configure Netlify CMS we create a `config.yml` file in the same directory:
```
backend:
  name: github
  repo: lbischof/hugo-techlab-demo

media_folder: /static/images/uploads
public_folder: /images/uploads

collections:
  - name: labs
    label: Labs
    folder: content/labs
    fields:
      - label: Title
        name: title
        widget: string
      - label: Content
        name: body
        widget: markdown
```
Make sure to update your own Git repository under `repo:`.

After pushing the files the CMS should be reachable under `yoursite.netlify.app/admin`.

See the [Netlify CMS documentation](https://www.netlifycms.org/docs/configuration-options/) for a full reference regarding all the different configuration options.

---

**Ende Lab 10**

<!--<p width="100px" align="right"><a href="08_assets.md">Assets →</a></p>-->

[← back to the overview](../README.md)
