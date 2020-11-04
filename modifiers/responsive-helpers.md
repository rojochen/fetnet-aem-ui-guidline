# Responsive helpers

Display utility classes that apply to all [breakpoints](https://getbootstrap.com/docs/4.3/layout/overview/#responsive-breakpoints), from `xs` to `xl`, have no breakpoint abbreviation in them. This is because those classes are applied from `min-width: 0;` and up, and thus are not bound by a media query. The remaining breakpoints, however, do include a breakpoint abbreviation.

As such, the classes are named using the format:

* `.d-{value}` for `xs`
* `.d-{breakpoint}-{value}` for `sm`, `md`, `lg`, and `xl`.

Where _value_ is one of:

* `none`
* `inline`
* `inline-block`
* `block`
* `table`
* `table-cell`
* `table-row`
* `flex`
* `inline-flex`

The display values can be altered by changing the `$displays` variable and recompiling the SCSS.

The media queries effect screen widths with the given breakpoint _or larger_. For example, `.d-lg-none` sets `display: none;` on both `lg` and `xl` screens.

