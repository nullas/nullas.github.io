---
date: '2025-03-08T13:11:35-08:00'
title: 'Hugo Setup with PaperMod and MathJax on GitHub Pages'
---
## tl;dr

In case I forgot how to figure Hugo, the procedure to set up Hugo with the PaperMod theme on GitHub Pages. MathJax is also enabled and VS code integration with Markdown+Math extension.

### Install Hugo

Install Hugo via Go

```go install github.com/gohugoio/hugo@latest```

I learnt that Linux Mint is so stable that its Golang version is still 1.22,
which doesn't satisfy the minimal requirement of latest Hugo. The same for
Hugo. So I have to install Golang and Hugo from their sources.

### Create the New Site

Run to create a new site.

```shell
hugo new site nullas.github.io --format yaml --force
```

`--force` is added because I had an existing site at nullas.github.io.

### Install the PaperMod Theme

Add the following config in `hugo.yaml`.

```
theme: ["PaperMod"]
```

Clone the PaperMod these repository.

```shell
git submodule add --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

### Enable MathJax

Escape the brackets as delimiters for Tex. Add the following to `hugo.yaml`.

```yaml
markup:
  goldmark:
    extensions:
      passthrough:
        delimiters:
          block:
          - - \[
            - \]
          - - $$
            - $$
          inline:
          - - \(
            - \)
        enable: true
```

Create `layouts/partials/math.html` with the following content

```html
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>
<script>
  MathJax = {
    tex: {
      displayMath: [['\\[', '\\]'], ['$$', '$$']],  // block
      inlineMath: [['\\(', '\\)']]                  // inline
    },
    loader:{
      load: ['ui/safe']
    },
  };
</script>
```

Create `layouts/partials/extend_head.html` with the following content to inject `layouts/partials/math.html` to all pages. (I don't care it might take longer for the site to load.)

```
{{ partial "math.html" . }}
```

### Deploy with GitHub Actions

Exclude the `public/` directory, which is built by Hugo locally by
adding it to `.gitignore`.

```
public/
```

Create an action to build the static site by creating
`.github/workflows/hugo.yaml` with the content [here](https://gohugo.io/host-and-deploy/host-on-github-pages/#step-6).
Mind to change the
Hugo version and branch.

