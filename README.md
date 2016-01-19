Beard Template Engine
=======

Blazing fast, [open source](https://github.com/zalando/beard), logic-less template engine written in Scala, used to parse templates using a simple syntax:

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


What makes Beard special:

  - simple syntax: inspired by mustache, we only use the {{ and }} markers for tags
  - streaming: as soon as we have something to be rendered, we are able to stream it to the browser. This gives high user perceived performance.
  - fast: have benchmarked it against other jvm template engines, and we strive to keep it on top. Check out our [repository](https://github.com/zalando/beard) to run the benchmarks.
  - beautiful: only using brackets for delimiters keeps it beautiful