# Data Types
- string (e.g. "Hello world", kittens)
- number (e.g. 42, 1337px)
- color (e.g. hotpink, rgb(1, 33, 7), #BADA55)
- list (e.g. (a, b, c), a b c)
- map (e.g. (a: 1, b: 2))
- bool (true or false)
- null (null)

## Strings
`$my-variable: 'Hello world!';`
```
$font-name: 'Helvetica';
$font-type: sans-serif;
.foo {
  font-family: $helvetica, $font-type;
}
```

```
$base-path: '/images/';
$file-name: 'kittens';
$extension: 'png';
$file-path: $base-path + $file-name + '.' + $extension;
// -> '/images/kittens.png'
```

## Numbers
```
$container-max-width: 1180px;
.container {
  width: 100%;
  margin: 0 auto;
  max-width: $container-max-width;
}
```

```
$element-width: 400px;
/**
* 1. Size the element
* 2. Horizontally center the element in its container
* @TODO: move to CSS transforms once we drop support for IE 8
*/
.foo {
  width: $element-width; /* 1 */
  position: absolute; /* 2 */
  left: 50%; /* 2 */
  margin-left: ($element-width / -2); /* 2 */
}
```
```
.foo {
  $gap: 20px;
  // No variable nor parentheses: no division performed
  font: 16px / 2 sans-serif;
  // Wrapping parentheses: division returning 8px
  padding: (16px / 2);
  // Member as variable: division returning 10px
  margin: $gap / 2;
  // Arithmetic expression: calculation returning 308px
  width: 300px + 16px / 2;
}
```
### Units
```
$value: 42;
$good: $value * 1px;
$bad: $value + px;
```
```
$initial-value: 42;
$value-in-px: ($initial-value * 1px); // 42px
$unitless-value: ($value-in-px / 1px); // 42
```

## Colors
```
$brand-color: #BADA55;
.logo {
  color: $brand-color;
}
```
```
.message {
  padding: 10px;
  border: 1px solid currentcolor;
}
.message-info {
$color: blue;
  color: $color;
  background-color: lighten($color, 20%);
}
.message-danger {
  $color: red;
  color: $color;
  background-color: lighten($color, 20%);
}
.message-confirm {
$color: green;
  color: $color;
  background-color: lighten($color, 20%);
}
```
## Booleans
```
$support-legacy-browsers: true;
@if $support-legacy-browsers {
  .clearfix {
    *zoom: 1;
  }
}
```
```
.clearfix:after {
  content: '';
  display: table;
  clear: both;
} 
``` 

### The not keyword
```
$bool: false;
// "if not false"
// which can be rewritten as: "if true"
@if not $bool {
  // We get in there
}
```

## Null
```
$type: type-of(null); // null
$type: type-of(NULL); // string
$type: type-of('null'); // string
$type: type-of('n' + 'u' + 'LL'); // string
```
```
$value: null;
.foo {
  // This declaration will not be output since
  24 Jump Start Sass
  // the variable is evaluated as `null`
  color: $value;
}
```

```
@mixin absolute($top: null, $right: null, $bottom: null, $left: null) {
  position: absolute;
  top: $top;
  right: $right;
  bottom: $bottom;
  left: $left;
}
```
```
.foo {
  @include absolute($top: 13px, $left: 37px);
}
```
```
.foo {
  position: absolute;
  top: 13px;
  left: 37px;
}
```

## Lists
```
$list: (42, hotpink, 'kittens');
```
```
$empty-list: ();
```
```
$value: Hello world;
$type: type-of($value); // list
$length: length($value); // 2
$separator: list-separator($value); // space
```
```
$value: ('Hello', 'world');
$type: type-of($value); // list
$length: length($value); // 2
$separator: list-separator($value); // comma
```
```
$value: 'foo';
$length: length($value); // 1
$type: type-of($value); // string
```
```
$value: ('foo',);
$length: length($value); // 1
$type: type-of($value); // list
```


