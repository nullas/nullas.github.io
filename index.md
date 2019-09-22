---
title: Xin's Blog.
---

## Blogs

{% for p in site.posts %}
### [{{ p.title }}]({{ p.url }})

{{ p.excerpt }}
---
{% endfor %}

## Study Notes.

{% for p in site.pages %}
[{{ p.title }}]({{ p.url }})
{% endfor %}
