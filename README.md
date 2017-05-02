**Media Queries Made Simple**

PiecewiseCSS makes use of an intuitive responsive design pattern to make writing Sass for different screen sizes easy and fast.

`main.scss`
```js
import '../node_modules/piecewisecss/piecewise';

h1 {
    @include piecewise(font-size, 24, 48, 480, 1200, !important);
}
```

The piecewise mixin takes six arguments:
1. a CSS property;
2. the minimum 
3. and maximum desired values of that property (in px);
4. the browser widths, beneath
5. and above which those values will be applied;
6. and an optional appender argument for values such as `!important`.

In the example above, the `<h1>` tag will have:
* a `font-size` of `24px` at browser width <= `480px`;
* a `font-size` of `48px` at browser width >= `1200px`;
* between `480px` and `1200px`, the font-size will be scaled linearly with the browser width, resulting in smooth, cojoining media queries and breakpoints.