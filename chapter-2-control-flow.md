# Control Flow

## If Statement

Here is a simple if statement:
```html
<html>
  <body>
    {{if user.isCool}}
      <div>{{user.name}} is cool</div>
    {{/if}}
  </body>
</html>
```

You can use an else:
```html
<html>
  <body>
    {{if user.isCool}}
      <div>{{user.name}} is cool</div>
    {{else}}
      <div>{{user.name}} is not cool</div>
    {{/if}}
  </body>
</html>
```

## For Statement

Here is a simple for statement:
```html
<div>
  {{for user in users}}
    <div>Hello {{user.name]}</div>
  {{/for}}
</div>
```

You can expose the index of the current iteration by following the syntax `{{for element, index in collection}}`):
```html
<ul>
{{for user, index in users}}
<li>{{index}} - Hello {{user.name}}</li>
{{/for}}
</ul>
```

Inside of the for, we expose some helpers: `isFirst`, `isLast`, `isNotLast`, `isOdd`, `isEven`. Here how to use them:

```html
<div>
  {{for user in users}}
    <span>{{user.name}}</span>
    <span>isFirst: {{user.isFirst}}</span>
    <span>isLast: {{user.isLast}}</span>
    <span>isNotLast: {{user.isNotLast}}</span>
    <span>isOdd: {{user.isOdd}}</span>
    <span>isEven: {{user.isEven}}</span>
  {{/for}}
</div>
```

Of course, you can use these helpers inside ifs:

```html
<div>
  {{for user in users}}
    {{if user.isOdd }}
      <span clas="red">{{user.name]} </span>
    {{else}}
      <span class="white">{{user.name}}</span>
    {{/if}}
  {{/for}}
</div>
```

