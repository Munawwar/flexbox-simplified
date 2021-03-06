# flexbox-simplified
Just two mixins, to flexbox like a pro!

We used this a lot in the codebase for two large e-commerce websites in the UAE - nisnass.ae and ounass.ae

## Documentation
```
horizontal-children(verticalAlignment, justify, wrapBehavior);
vertical-children(horizontalAlignment, justify);
```

`verticalAlignment` and `horizontalAlignment` can be one of the three values: flex-start, flex-end or center

`justify` can be one of four values: flex-start, flex-end, center or stretch

`wrapBehavior` defaults to `wrap`. You can override it with `nowrap`

(Other CSS props like baseline, space-between, space-around and space-evenly hasn't been tested)

In additon to this, you need to know how to use flex-grow, flex-shrink and flex-basis to make your layout (learn it from CSS docs elsewhere).

## Example
Let's make 3 horizontally aligned boxes and make parent horizontally scrollable.

HTML
```html
<body>
  <div class="parent">
    <div class="box1">Box 1</div>
    <div class="box2">Box 2</div>
    <div class="box3">Box 3</div>
  </div>
</body>
```

SASS
```scss
body {
  @include vertical-children(stretch);
}
.parent {
  flex: 1 0 auto; // short hand for flex-grow: 1; flex-shrink: 0; flex-basis: auto;
  // which means "grow beyond content width (if space is available), but
  // don't allow shrinking below content width"
  @include horizontal-children(stretch, flex-start, nowrap);
  overflow-x: scroll; // not needed.. but being explicit
}
.box1, .box2, .box3 {
  flex: 1 0 auto;
  width: 60vw;
  @include vertical-children(center, center);
}
```

That's it. You can become a flexbox ninja now.
