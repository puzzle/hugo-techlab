# Lab 7: Partials
Partial templates allow you to introduce modularity into your website. They let you break your website down into individual components and then insert those components into layouts to create the site.

Creating partial templates allows us to split our templates. It separates the website into smaller parts making it easier to manage. We can now tweak and change individual parts of the website without having to change or affect everything else. This is good design.

## Create a Partial
The partial located at `themes/mytheme/layouts/partials/head.html` is already included in the `layouts/_default/baseof.html` template. So we can add some content:
```
<head>
  <title>{{ .Site.Title }}</title>
</head>
```
And it should just work.

## Access Variables Inside a Partial
In a hugo layout we can access the front matter page parameters using `.Params`. The dot represents the scope of all values associated with the given page. In order to access the front matter parameters in our partials we must pass in the scope of the page (represented by the dot) like this:

```
{{ partial "head.html" . }}
```
It is also possible to pass custom values. An easy way to do this is by creating and passing in a dict. Dict is short for dictionary and contains a series of key value pairs.

```
{{ partial "head.html" (dict "color" "blue" )}}
```
The color is then available inside the partial with `{{ .color }}`.

It is possible to add more key value pairs:
```
{{ partial "head.html" (dict "color" "blue" "width" 10 )}}
```


## Conclusion
Partials allow a lot of modularity and flexibility. Instead of copying a template, we can reuse it in multiple places.

---

**Ende Lab 7**

<p width="100px" align="right"><a href="08_assets.md">Assets →</a></p>

[← back to the overview](../README.md)
