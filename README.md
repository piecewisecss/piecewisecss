**Media Queries Made Simple**

PiecewiseCSS makes use of an intuitive responsive design pattern to make writing Sass for all screen sizes fast and easy.

`main.scss`

```js
import '../node_modules/piecewisecss/piecewise.scss';

h1 {
    @include piecewise(font-size, 24, 48, 480, 1200, !important);
}
```

The `piecewise()` mixin takes six arguments:

1. a CSS property;
2. the minimum
3. and maximum desired values of that property (in px);
4. the browser widths, beneath
5. and above which those values will be applied;
6. and an optional appender argument for values such as `!important`.

In the example above, the `<h1>` tag will have:

* a `font-size` of `24px` at browser width <= `480px`;
* a `font-size` of `48px` at browser width >= `1200px`;
* between `480px` and `1200px`, the font-size will be scaled linearly with the browser width, resulting in a seamless, gradual breakpoint.

**Global Breakpoint Variables**

New in **1.4**! Use global variables to keep your breakpoints consistent. Using one or both of the local width arguments will override these.

`main.scss`
```js
$globalMin: 480px;
$globalMax: 1000px;
```
`some other file`
```js
.class {
    @include piecewise(padding: 0 5px, 20px);
}
```

**Use as Breakpoint**

```js
.class {
    @include piecewise(flex-basis, 100%, 33%, 480);
}
```

New in **1.2**! The fifth `pxMax` argument is now optional, allowing you to invoke `piecewise()` to apply one-line media queries. In the example above, `flex-basis` will simply flip from `100%` to `33%` at `480px`.
