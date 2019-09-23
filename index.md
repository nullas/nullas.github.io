---
title: Xin's Blog.
layout: page
---

## Blogs

{% for p in site.posts %}
### [{{ p.title }}]({{ p.url }})

{{ p.excerpt }}
{% endfor %}

## Study Notes.

{% assign notes = site.pages | where: "dir", "/notes/" %}
{% for p in notes %}
[{{ p.title }}]({{ p.url }})
{% endfor %}
