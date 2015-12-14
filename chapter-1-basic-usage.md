# Basic Usage

Here is a really simple example, to render an `index` template:

```html
<html>
  <head>
	<title>{{ the.title }}</title>
  </head>
  <body>
	{{ the.content }}
  </body>
</html>
```

In order to be able to render it, we need to be able to load it, so we'll define a template loader:

```scala
val loader = new ClasspathTemplateLoader(
  templatePrefix = "/templates",
  templateSuffix = ".beard"
)
```

Then, we need to compile the template:

```scala
val templateCompiler = new CustomizableTemplateCompiler(templateLoader = loader)
val template = templateCompiler.compile(TemplateName("index")).get
```

We also need a context:
```scala
val context: Map[String, Map[String, Object]] = Map("the" -> Map("title" -> "Title", "content" -> "Content"))
```

Now it's time to render it:

```scala
val renderer = new BeardTemplateRenderer(templateCompiler)
val result = renderer.render(template,
  StringWriterRenderResult(),
  context,
  Some(applicationLayout))
```

As we expect we'll end up with this:

```html
<html>
  <head>
	<title>Title</title>
  </head>
  <body>
	Content
  </body>
</html>
```