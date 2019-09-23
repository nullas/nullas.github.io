---


---


I am using [StackEdit](https://stackedit.io/) to render markdown with $$\LaTeX$$. StackEdit uses a single dollar sign \$ for inline math block. However, Kramdown does not support the single dollar sign for inline math block. Kramdown use double dollar design \$\$ to denote both inline and display math block. To be able to publish MarkDown from Stackedit to GitHub pages as .md, instead of as .html, inline math block quoted by a single dollar sign in StackEdit has to be converted to double dollar sign. To do this, we can leverage StackEdit helpers. Add a helper like this

```javascript
Handlebars.registerHelper('transformMathJax',  function  (options)  {  
var result = options.fn(this);  
return  new  Handlebars.SafeString(  
result.replace(/(?<![\$\\])\$(?!\$)/g,  '$$$$')  
);  
});
```

and publisher it like

```yaml
---  
{{{files.0.content.yamlProperties}}}  
---  
  
{{#transformMathJax}}{{{files.0.content.text}}}{{/transformMathJax}}
```
> Written with [StackEdit](https://stackedit.io/).

