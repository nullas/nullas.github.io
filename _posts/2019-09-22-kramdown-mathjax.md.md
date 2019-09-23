---


---


I am using [StackEdit](https://stackedit.io/) to render markdown with $$\LaTeX$$. StackEdit uses a single dollar sign \$ for inline math block. However, Kramdown does not support the single dollar sign for inline math block. Kramdown use double dollar design \$\$ to denote both inline and display math block. To be able to publish MarkDown from Stackedit to GitHub pages as .md, instead of as .html, inline math block quoted by a single dollar sign in StackEdit has to be converted to double dollar sign. To do this, we can leverage StackEdit helpers. Add a helper like this,

```javascript

```

> Written with [StackEdit](https://stackedit.io/).

