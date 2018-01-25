## **Seamless Media Queries Made Simple**

PiecewiseCSS makes use of an intuitive responsive design pattern to make writing Sass for all screen sizes fast and easy.

`main.scss`

```scss
@import '../node_modules/piecewisecss/piecewise.scss';

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

## **Global Breakpoint Variables**

**New in 1.4:** Use global variables to keep your breakpoints consistent. Using one or both of the local screen width arguments will override these.

`main.scss`

```scss
$globalMin: 480px;
$globalMax: 1000px;
```

`./some-other-file.scss`

```scss
@import './main.scss';
.class {
    @include piecewise(padding: 0 5px, 20px);
}
```

## **Use as Breakpoint**

**New in 1.2:** Invoke `piecewise()` to apply one-line media queries by using only the `pxMin` argument. In the example below, `flex-basis` will simply flip from `100%` to `33%` at `480px`.

```scss
.class {
    @include piecewise(flex-basis, 100%, 33%, 480);
    @include piecewise(flex-direction, column, row, 480);
}
```

Note this is the only mode of `piecewise()` that supports non-`px` and string values.

## **@inversePiecewise()**

**New in 1.5:** The @mixin `inversePiecewise()` provides you with the inverse value (100% - that value) of what `piecewise()` provides you. Say you want control of two divs that split the width of a parent:

```scss
.sidebar {
    @include piecewise(width, 100, 120, 480, 1000);
}
.window {
    @include inversePiecewise(width, 100, 120, 480, 1000);
}
```

In this example, `.sidebar` will adjust its width from `100px` to `120px` from view-widths `480px` to `1000px`, and the `.window` element will occupy the rest of the remaining space.

## On, Off, On Again ##

**New in 1.7:** Invoke `piecewise()` to set three values at two breakpoints:

```scss
@include piecewise(display, none, inline, none, 650, 1000);
```

This element will be displayed inline between `650px` and `1000px`, and disappear otherwise.
