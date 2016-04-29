# Filters

In this section we introduce the available filters and how are they applied to values or collections with examples. Note that mostly for collections the filter are applied singularly to each value in the collection, exceptions are First, Last and Reverse.

## Abs Filter

The abs filter will return the absolute value of a number:

```scala
val integer = -10
val list = List(1, 2 , -9, -4)
val map = Map(1 -> -4, 2 -> 9)
```
```html
<div>{{ integer | abs }}</div>
<div>{{ list | abs }}</div>
<div>{{ map | abs }}</div>
```

Will be rendered has:

```html
<div>10</div>
<div>1,2,9,4</div>
<div>(1,4),(2,9)</div>
```

## Capitalize Filter

The Capitalize filter will turn the first char of a string to uppercase:

```scala
val string = "word"
val list = List("word1", "word2")
val map = Map(1 -> "word1", 2 -> "word2")
```
```html
<div>{{ string | capitalize }}</div>
<div>{{ list | capitalize }}</div>
<div>{{ map | capitalize }}</div>
```

Will be rendered has:

```html
<div>Word</div>
<div>Word1,Word2</div>
<div>(1,Word1),(2,Word2)</div>
```

## Currency Filter

The currency filter will format a number into a currency, optionally you can specify a symbol and a format parameter:

```scala
val integer = 10
val list = List(1, 2.25, 9.67, 4)
val map = Map(1 -> 4.67, 2 -> 9.88)
```
```html
<div>{{ integer | currency }}</div>
<div>{{ integer | currency symbol="GBP" }}</div>
<div>{{ list | currency format="#.0 ¤" symbol="GBP" }}</div>
<div>{{ map | currency format="#.00 ¤" symbol="€" }}</div>
```

Will be rendered has:

```html
<div>$10</div>
<div>GBP10</div>
<div>1 GBP,2.3 GBP,9.7 GBP,4 GBP</div>
<div>(1,4.67 €),(2,9.88 €)</div>
```

## Date Format Filter

The date format filter will turn a value to a date depending on the specified format:

```scala
val date = "3-12-2001"
val list = List("3-12-2001", "3-9-2012")
val map = Map(1 -> "3-12-2001", 2 -> "3-9-2012")
```
```html
<div>{{ date | date format yyyy-MM-dd }}</div>
<div>{{ list | date format yyyy-MM-dd }}</div>
<div>{{ map | date format yyyy-MM-dd }}</div>
```

Will be rendered has:

```html
<div>2001-12-3</div>
<div>2001-12-3,2012-9-3</div>
<div>(1,2001-12-3),(2,2012-9-3)</div>
```

Supported formats are:

- EPOCH
- EPOCH_MILLI
- yyyyMMdd
- yyyy-MM-dd HH:mm:ss
- yyyy-MM-dd HH:mm:ssZ
- yyyy-MM-dd
- ISO_OFFSET_DATE
- ISO_LOCAL_DATE_TIME
- ISO_OFFSET_DATE_TIME
- ISO_INSTANT
- ISO_INSTANT
- yyyy-M-dd
- yyyy-MM-d
- yyyy-M-d
- dd-MM-yyyy
- dd-MM-yyyy HH:mm:ss
- d-MM-yyyy
- dd-M-yyyy
- d-M-yyyy
- HH:mm:ss

## First Filter

The first filter will return the first char of a string or the first element of a collection:

```scala
val string = "Hello World!"
val list = List("fist", "second", "third")
val map = Map(1 -> "first", 2 -> "second")
```
```html
<div>{{ string | first }}</div>
<div>{{ list | first }}</div>
<div>{{ map | first }}</div>
```

Will be rendered has:

```html
<div>H</div>
<div>first</div>
<div>(1,first)</div>
```

Note that this throws an exception if the string or collection is empty.

## Last Filter

The last filter will return the last char of a string or the last element of a collection:

```scala
val string = "Hello World!"
val list = List("fist", "second", "third")
val map = Map(1 -> "first", 2 -> "second")
```
```html
<div>{{ string | last }}</div>
<div>{{ list | last }}</div>
<div>{{ map | last }}</div>
```

Will be rendered has:

```html
<div>!</div>
<div>third</div>
<div>(2,second)</div>
```

Note that this throws an exception if the string or collection is empty.

## Lowercase Filter

The lower case filter will turn a string to lower case:

```scala
val string = "Hello"
val list = List("Fist", "SECOND", "Third")
val map = Map(1 -> "first", 2 -> "Second")
```
```html
<div>{{ string | lowercase }}</div>
<div>{{ list | lowercase }}</div>
<div>{{ map | lowercase }}</div>
```

Will be rendered has:

```html
<div>hello</div>
<div>first,second,third</div>
<div>(2,first),(2,second)</div>
```

## Number Filter

The number filter will format a number according to the provided format if one is provided:

```scala
val number = 12.29
val list = List(12.29, 56.7)
val map = Map(1 -> 12.29, 2 -> 56.7)
```
```html
<div>{{ number| number }}</div>
<div>{{ number| number format="0.0" }}</div>
<div>{{ number| number format="#.0 ¤" }}</div>
<div>{{ number| number format="#.00 €" }}</div>
<div>{{ list | number format="#.0 ¤" }}</div>
<div>{{ map | number format="0.0" }}</div>
```

Will be rendered has:

```html
<div>12.29</div>
<div>12.3</div>
<div>12.3 $</div>
<div>12.29 €</div>
<div>12.3 $,56.7 $</div>
<div>(2,12.3),(2,56.7)</div>
```

## Reverse Filter

The reverse filter will reverse a string or a collection:

```scala
val string = "reverseme"
val list = List("hello", "world")
val map = Map(1 -> "hello", 2 -> "world")
```
```html
<div>{{ string| reverse }}</div>
<div>{{ list | reverse }}</div>
<div>{{ map | reverse }}</div>
```

Will be rendered has:

```html
<div>emesrever</div>
<div>world,hello</div>
<div>(2,world),(1,hello)</div>
```

Note that this will throw on empty collections.

## Translation Filter

The translation filter will attempt to translate a string with a provided bundle:

```scala
val string = "hello"
val list = List("hello", "world")
val map = Map(1 -> "hello", 2 -> "world")
```
```html
<div>{{ string| translate bundle="messages" locale="de"}}</div>
<div>{{ list | translate bundle="messages" locale="it" }}</div>
<div>{{ map | translate bundle="messages" locale="de" }}</div>
```

Will be rendered has:

```html
<div>hallo</div>
<div>ciao, mondo</div>
<div>(1, hallo),(2,welt)</div>
```


## Title Filter

The title filter will capitalize each word in a string separated by space:

```scala
val string = "hello world"
val list = List("hello", "world")
val map = Map(1 -> "hello", 2 -> "world")
```
```html
<div>{{ string| title }}</div>
<div>{{ list | title }}</div>
<div>{{ map | title }}</div>
```

Will be rendered has:

```html
<div>Hello World</div>
<div>Hello, World</div>
<div>(1,Hello),(2,World)</div>
```

## Trim Filter

The trim filter will trim a string:

```scala
val string = "hello world    "
val list = List("  hello", "world  ")
val map = Map(1 -> "hello  ", 2 -> " world")
```
```html
<div>{{ string| title }}</div>
<div>{{ list | title  }}</div>
<div>{{ map | title  }}</div>
```

Will be rendered has:

```html
<div>hello world</div>
<div>hello, world</div>
<div>(1,hello),(2,world)</div>
```

## Uppercase Filter

The upper case filter will turn a string to upper case:

```scala
val string = "hello"
val list = List("fist", "second", "THIRD")
val map = Map(1 -> "first", 2 -> "second")
```
```html
<div>{{ string | uppercase }}</div>
<div>{{ list | uppercase }}</div>
<div>{{ map | uppercase }}</div>
```

Will be rendered has:

```html
<div>HELLO</div>
<div>FIRST,SECOND,THIRD</div>
<div>(2,FIRST),(2,SECOND)</div>
```

## Url Encode Filter Filter

The url encode filter encode a string in UTF-8:

```scala
val url = "https://github.com/danpersa/beard-book"
val list = List("https://github.com/danpersa/beard-book", "https://www.google.com")
val map = Map(1 -> "https://github.com/danpersa/beard-book", 2 -> "https://www.google.com")
```
```html
<div>{{ string | uppercase }}</div>
<div>{{ list | uppercase }}</div>
<div>{{ map | uppercase }}</div>
```

Will be rendered has:

```html
<div>https%3A%2F%2Fgithub.com%2Fdanpersa%2Fbeard-book</div>
<div>https%3A%2F%2Fgithub.com%2Fdanpersa%2Fbeard-book,https%3A%2F%2Fwww.google.com</div>
<div>(1,https%3A%2F%2Fgithub.com%2Fdanpersa%2Fbeard-book),(2,https%3A%2F%2Fwww.google.com)</div>
```

## Custom Filters

Users have the possibility to create their own filters by simply extending the `Filter` trait:

```scala
class FunkyFilter extends Filter {
  override def name: String = "funky"

  override def apply(value: String, parameters: Map[String, Any]): String =
    "Don't forget to boogie!"
}
```

 Where `name` is the name of your filter and the string you have to use in your template to identify the filter. What this filter does is transform everything to the string `Don't forget to boogie!`. Optionally you can also override `applyIterable` and `applyMap` if you want to customize behaviour for collections. You can then add your filter when instantiating a filter resolver:

```scala
val filterResolverWithFunky = new DefaultFilterResolver(Seq(funkyFilter))
```