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
{{# This is an inline comment #}}
{{# This is
a multiline comment
#}}
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
Inside of the for, we expose some helpers: `isFirst`, `isLast`, `isOdd`, `isEven`. Here is how to use them:
```html
<ul>
{{for user in users}}
<li {{if user.isFirst}}class="first"{{/if}}>
Hello {{user.name}}
</li>
{{/for}}
</ul>
```

You can expose the index of the current iteration by following the syntax `{{for element, index in collection}}`):
```html
<ul>
{{for user, index in users}}
<li>{{index}} - Hello {{user.name}}</li>
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
Marks one fraction of the code as a block, so it can be [extended](#extends-statement).
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
When [extending](#extends) a template, the content that is not included withing a [block statement](#block-statement) will be yielded under the [yield statement](#yield-statement).
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

## Extends Statement
Extends a template, **contentFor** statements overwrites the [block statement](#block-statement) with the matching name. The rest of the content not marked as **contentFor** will be yielded under the [yield statement](#yield-statement).
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
<p>Yielded content</p>
```