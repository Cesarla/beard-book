# Quick Reference

## Interpolation
```html
<ul>
  <li>Basic Interpolation: {{name}}</li>
  <li>Complex Interpolation {{user.name}}</li>
</ul>
```

## Comment Statement
```html
{{comment}}JS Dependancies.{{/comment}}
<script type="text/javascript" async="" src="http://www.google-analytics.com/ga.js"></script>
```

## If Statement
```html
<p>
{{if user.isCool}}
This is cool
{{else}}
This is not cool
{{/if}}
</p>
```

## For Statement
Inside of the for, we expose some helpers: `isFirst`, `isLast`, `isOdd`, `isEven`. Here how to use them:
```html
<ul>
{{for user in users}}
<li {{if user.isFirst}}class="first"{{/if}}>
Hello {{user.name}}
</li>
{{/for}}
</ul>
```

## Render Statement
```html
<html>
  <header>
    {{ render "/templates/_css.beard" }}
  </header>
  <body>
  </body>
  {{ render "/templates/_js.beard" }}
</html>
```

## Block Statement
Marks one fraction of the code as block, so it can be [extended](#Extends).
```html
<html>
  <body>
    {{block header}}
      application header
    {{/block}}
  </body>
<html>
```

## Yield Statement
When [extending](#Extends) a template, the content that is not included withing a block will be yielded under the {{yield}} statement.
```html
<html>
  <body>
    {{block header}}
      application header
    {{/block}}
    {{yield}}
  </body>
<html>
```

## Extends
```html
{{extends "/beard-benchmark/double-column.beard"}}
{{contentFor header}}
<nav class="top-navi">
  <ul>
    <li>First Link</li>
    <li>Second Link</li>
    <li>Third Link</li>
  </ul>
</nav>
{{/contentFor}}
