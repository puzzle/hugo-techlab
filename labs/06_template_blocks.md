# Lab 6: Template Blocks

The base and block constructs allow you to define the outer shell of your templates.

The theme already includes a basic base template in `layouts/_default/baseof.html`:

```
<!DOCTYPE html>
<html>
    {{- partial "head.html" . -}}
    <body>
        {{- partial "header.html" . -}}
        <div id="content">
        {{- block "main" . }}{{- end }}
        </div>
        {{- partial "footer.html" . -}}
    </body>
</html>
```

The block keyword behaves like a function that accepts two arguments:
1. the name of the block
2. the current variable scope (`.`) so it is available inside the block

A block defines the location where another template can insert itself.

## Update Homepage to use the Base Template
Now we want to insert our homepage template into the "main" block. We can achieve this by surrounding our template with `{{ define "main" }}`:
```
{{ define "main" }}
  <h1>homepage</h1>

  {{ range .Site.RegularPages }}
    <h2>
      <a href="{{ .Permalink }}">{{ .Title }}</a>
    </h2>
  {{ end }}
{{ end }}
```
Check if everything worked:
```
$ hugo
$ cat public/index.html
<!DOCTYPE html>
<html><body><div id="content">
<h1>homepage</h1>
  <h2>
    <a href="http://example.org/labs/01_quicktour/">1. Quicktour</a>
  </h2>
</div></body>
</html>
```

## Exercise: Update the Page Template to use the Base Template
In the last lab we created a template that renders a single page. This template should also use the base template.

<details>
  <summary>Solution</summary>

  Update the file `./themes/mytheme/layouts/_default/single.html`:
  ```
  {{ define "main" }}
    <h1>{{ .Title }}</h1>
    {{ .Content }}
  {{ end }}
  ```
  And then run `hugo`.
</details>

The file `public/labs/01_quicktour/index.html` should now be surrounded with a `<html>` tag.

## Conclusion

Our small website is slowly taking shape. In the next lab we will learn about partials. These can be included in multiple templates and ensure that template code only needs to be written once.

---

**Ende Lab 6**

<p width="100px" align="right"><a href="07_partials.md">Partials →</a></p>

[← back to the overview](../README.md)
