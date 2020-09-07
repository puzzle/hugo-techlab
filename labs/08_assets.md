# Lab 8: Assets

Assets are Javascript, stylesheets and images. These assets can either be served directly without modification or Hugo can process them.

## Static Files

By default, the `static/` directory in the site project is used for all _static files_ (e.g. stylesheets, JavaScript, images). The static files are served on the site root path (eg. if you have the file `static/image.png` you can access it using `http://{server-url}/image.png`, to include it in a document you can use `![Example image](/image.png)` ).

## Resources

Hugo also supports processing files. For example it is possible to convert Sass to CSS or bundle multiple files into one.

For this assets must be stored in the `assets/` directory. In order to process an asset with Hugo Pipes, it must be retrieved as a resource using `resources.Get`, which takes one argument: the filepath of the file relative to the asset directory.

Example (see below for more information):
```
{{ $style := resources.Get "sass/main.scss" | resources.ToCSS | resources.Minify | resources.Fingerprint }}
<link rel="stylesheet" href="{{ $style.Permalink }}">
```
Assets will only be published (to `./public`) if `.Permalink` is used.

### ToCSS
Any SASS or SCSS file can be transformed into a CSS file using `| resources.ToCSS`. See the [Hugo docs](https://gohugo.io/hugo-pipes/scss-sass/) for more information.

### Babel
Any JavaScript resource file can be transpiled to another JavaScript version using `| resources.Babel`. See the [Hugo docs](https://gohugo.io/hugo-pipes/babel/) for more information.

### Minify
Any resource (CSS, JS, JSON, HTML, SVG or XML) can be minified using `| resources.Minify`.

### Concat
Asset files of the same MIME type can be bundled into one resource using `| resources.Concat`.
```
{{ $plugins := resources.Get "js/plugins.js" }}
{{ $global := resources.Get "js/global.js" }}
{{ $js := slice $plugins $global | resources.Concat "js/bundle.js" }}
<script src="{{ $js.Permalink }}"></script>
```

### Fingerprint
Fingerprinting can be applied to any asset file using `| resources.Fingerprint`. This is useful for caching. The Fingerprint changes every time the file is changed, thus invalidating the cache.

## Page Bundles

Instead of using the `assets` directory, resources can also be placed directly beside the content.
```
content/
├── about.md
└── posts
    └── my-post
        ├── image1.jpg
        ├── image2.png
        └── index.md
```

## Conclusion

---

**Ende Lab 8**

<p width="100px" align="right"><a href="09_deployment.md">Deployment →</a></p>

[← back to the overview](../README.md)
