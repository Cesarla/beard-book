# Render Statement

Let's say we have a template named `some-template` which looks like this:

```html
Hello {{ name }}! Your age is {{ age }}!
```

We want to include this template inside of another template. For this we use the `render` statement:

```html
{{ render "some-template" }}
```

Let's say we have the context:
```json
{
  "name": "Zorro",
  "age": 27,
  "leosAge": 32
}
```

The rendered template will loo like:

```
Hello Zorro! Your age is 27!
```

The `some-template` template is able to access the main context.

You're able to override or add values to the main context by using attributes:

```html
{{ render "some-template" name="Leo" age=leosAge }}
```

In this case, the rendered template will look like:

```
Hello Leo! Your age is 32!
```

As you can see, we define a new name, `Leo` and we replace the `age` with an existing value from the context, `leosAge`.

