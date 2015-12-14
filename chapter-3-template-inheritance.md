# Template Inheritance

We are able to define a base layout template, `layouts/application`, like this:

```html
<html>
  {{render "includes/head"}}
  <body>
    {{render "includes/header"}}
    <div id="main">
      {{yield}}
    </div>
    {{block footer}}Some default footer{{/block}}
    {{render "includes/scripts"}}
  </body>
<html>
```

Let's see what's happening here:
  - at the second line, we are including another template, the `includes/head` template
  - then, we include the `includes/header` template
  - at line 6, we have a `yield` keyword. The templates which extend our template, will be able to replace this, with their own stuff.
  - we also define a block at line 8, with a default text inside
  - in the end, we render the `includes/scripts` template, at line 9


And based on this initial layout we create a single column template:

```html
{{extends "layouts/application"}}

<div class="main-column">
  {{yield}}
</div>
```

You notice the `extends` statement as first statement. We use our initial layout as a base.

We also have another `yield` keyword. Again, the templates who extend our new template will be able to override it.

Let's go wild and create a two column template, `layouts/double-column`:

```html
{{extends "layouts/application"}}

{{contentFor footer}}
  This is some contentFor footer
{{/contentFor}}

<div class="navi">
  {{block navi}}
    <div id="navigation">Some navi here</div>
  {{/block}}
</div>
<div class="main-column">
  {{yield}}
</div> 
```

We use the same base template as a start. But in this case, we override the footer `block` we initially defined, using the `contentFor` directive.

And we define a new `block`, navigation, with some default value. Again templates who extend our template will be able to override it.

In the end, we use the `yield` again, to signal where the content from the template which will inherit from the current one will go.

Before now, we only created layout templates. Let's create two templates to be rendered, `home` and `about-us`

```html
{{contentFor footer}}
  This is the home specific contentFor footer
{{/contentFor}}

<div>Hello Index</div>
```

What we're doing here is that we override the footer block. What's interesting here, is that we don't extend a specific template. This is because beard let's you specify the layout at runtime:

```scala
    renderer.render(template, StringWriterRenderResult(), context, Some(applicationLayout))
```

Of course, you can specify the layout in the template, and here what we'll do for our `about-us` template:

```html
{{ extends "layouts/double-column" }}

{{contentFor navigation}}
  <ul>
    <li>Home</li>
    <li>About Us</li>
  </ul>
{{/contentFor}}

<div>About Us</div>
```

As we are using the `layouts/double-column` template as a base, we are able to override the navigation `block`.

