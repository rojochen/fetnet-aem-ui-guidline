# Space Helper

參照 [Bootstrap](https://getbootstrap.com/docs/4.3/utilities/spacing/) 的架構建置，使用方式如下：

The classes are named using the format `{property}{sides}-{size}` for `xs` and `{property}{sides}-{breakpoint}-{size}` for `sm`, `md`, `lg`, and `xl`.

Where _property_ is one of:

* `m` - for classes that set `margin`
* `p` - for classes that set `padding`

Where _sides_ is one of:

* `t` - for classes that set `margin-top` or `padding-top`
* `b` - for classes that set `margin-bottom` or `padding-bottom`
* `l` - for classes that set `margin-left` or `padding-left`
* `r` - for classes that set `margin-right` or `padding-right`
* `x` - for classes that set both `*-left` and `*-right`
* `y` - for classes that set both `*-top` and `*-bottom`
* blank - for classes that set a `margin` or `padding` on all 4 sides of the element

Where _size_ is one of:

* `0` - for classes that eliminate the `margin` or `padding` by setting it to `0`
* `1` - \(by default\) for classes that set the `margin` or `padding` to `$space * 1`
* `2` - \(by default\) for classes that set the `margin` or `padding` to `$space * 2`
* `3` - \(by default\) for classes that set the `margin` or `padding` to `$space * 3`
* `4` - \(by default\) for classes that set the `margin` or `padding` to `$space * 4`
* `5` - \(by default\) for classes that set the `margin` or `padding` to `$space * 5`
* `6` - \(by default\) for classes that set the `margin` or `padding` to `$space * 6`
* `7` - \(by default\) for classes that set the `margin` or `padding` to `$space * 7`
* `8` - \(by default\) for classes that set the `margin` or `padding` to `$space * 8`
* `9` - \(by default\) for classes that set the `margin` or `padding` to `$space * 9`
* `10` - \(by default\) for classes that set the `margin` or `padding` to `$space * 10`
* `auto` - for classes that set the `margin` to auto

### Example

```css
.mt-0 {
  margin-top: 0 !important;
}

.ml-1 {
  margin-left: ($space * 1) !important;
}

.px-2 {
  padding-left: ($space * 2) !important;
  padding-right: ($space * 2) !important;
}

.p-3 {
  padding: $space * 3 !important;
}
```

