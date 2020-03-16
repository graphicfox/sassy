# Grid
The grid system is one of the major features of the sassy library. As so many others it consists (by default) on a 12 column layout grid. Every grid column is separated from other columns using a gutter.
The items in your grid can but don't have to be wrapped into a container that centers your content on the screen. 

But why, if there are 14 bajilion other grids that do the same stuff you might ask. Because the sassy grid does not add a single css class, I say. The sassy grid consists of five sass mixins you can use in any of your application's sass code. 
So you don't end up with huge, unreadable "class" attributes and workarounds to apply the existing css to your requirements. The mixins will follow your lead and your coding guideline.

The grid is completely based on the [css flexbox layout](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), 
because [css grids](https://css-tricks.com/snippets/css/complete-guide-grid/) are still too unreliable for my liking :(

Contrary to the "bootstrap" approach where you have a "row" that contains columns you simply have a "grid" and "items" while using the sassy grid.
A grid can contain any number of items that define their "span" from 1 to 12. 

## Mixins

#### container()
A helper to convert the target element into a responsive container.
The content will be always centered on the page. The width of the content area can be configured globally.
If you need a special container size you can also override the global values by using the $override parameter

::: details Arguments
- $override A map containing the overrides for one or more breakpoints (xxs: 120px, xs: 260px,...)
:::

#### grid()
Creates a grid wrapper which can contain multiple grid items.
NOTE: You should NOT place items in this grid that have the +gridItemV mixin applied to them

::: details Arguments
- $gutterCompensation A valid gutter definition for sassyParseGutter() to change/disable
                    the automatic compensation of this grid's first and last rows of items. This is "auto" by default.
:::

#### gridItem()
Defines the element as a child of a default sassy grid.
NOTE: Items of this kind should ONLY be added to a grid that has the +gridItem mixin AND NOT the +gridItemV mixin applied to it

::: details Arguments
- $span The range this column should take up in its width.
      (Range: 1 - $sassyGridColumns / the value of options.of)
- $options Can take additional options for this item
    - of:     Can be used to override the default $sassyGridColumns value for this item
    - order:  The numeric order of this item in the element list
    - gutter: A valid gutter definition for sassyParseGutter() to change/disable
    the gutter of this child
    - offset: The column offset to the item that comes before this item
    - offsetAfter: The same as offset but applies to the item after this item
    - usePadding: By default the margin is used to create the gutters.
    If this conflicts with your use-case set this to true and the padding is used instead.
:::

#### gridV()
Creates a grid wrapper which can contain multiple grid items.
The difference to grid() is, that the wrapper compensates the vertical gutter for the first and
the last row of the grid and not only left and right.
NOTE: You should ONLY place items in this grid that have have the +gridItemV mixin applied to them.

::: details Arguments
- $gutterCompensation A valid gutter definition for sassyParseGutter() to change/disable
                    the automatic compensation of this grid's first and last rows of items. This is "auto" by default.
:::

#### gridItemV()
Defines the element as a child of a sassy grid with vertical gutter.
NOTE: Items of this kind should ONLY be added to a grid that has the +gridItemV applied to it

::: details Arguments
- $span The range this column should take up in its width.
      (Range: 1 - $sassyGridColumns / the value of options.of)
- $options Can take additional options for this item
    - of:     Can be used to override the default $sassyGridColumns value for this item
    - order:  The numeric order of this item in the element list
    - gutter: A valid gutter definition for sassyParseGutter() to change/disable
    the gutter of this child
    - offset: The column offset to the item that comes before this item
    - offsetAfter: The same as offset but applies to the item after this item
    - usePadding: By default the margin is used to create the gutters.
    If this conflicts with your use-case set this to true and the padding is used instead.
:::

## Container
A container is the main content area of your page.
It is centered horizontally in the viewport (or the parent container) and has a breakpoint aware width you can
configure in your configuration file if you wish to.

<Preview href="/examples/container" />

::: details CODE
```sass
.container
  +container
```

```html
<div class="container">
    <div>The responsive container</div>
</div>
```
:::

## Basic Grid
A grid is the outer wrapper for any number of grid items, it CAN but DOES NOT HAVE TO be placed inside a container.
By default a grid only has a horizontal gutter which can be configured using the config options.

<Preview href="/examples/gridBasic" :height="180"/>

::: details CODE
```sass
.container
  +container
  
// Create a grid, a grid is the outer wrapper for any number of grid items.
// A grid CAN but DOES NOT HAVE TO be placed inside a container
.grid
  +grid()

// Similar to bootstrap the sassy grid is by default
// split into 12 "columns" with margins "gutter" between them. 
// Without any options the item assumes it should
// take up all 12 columns
.fullWidthItem
  +gridItem(12)

// You can define the number of columns a single item should 
// take up using the first option
.splitLeftItem
  +gridItem(8)

// To fill up the row of 12 columns we need another 
// item with 4 additional columns
.splitRightItem
  +gridItem(4)
```

```html
<div class="container">
    <div class="grid">
        <div class="fullWidthItem">Full width</div>
        <div class="splitLeftItem">Left</div>
        <div class="splitRightItem">Right</div>
    </div>
</div>
```
:::

## Responsive Grid
When you are working responsively you need to modify the number of (columns) that your items take up for on different breakpoints.
This is where the breakpoint mixin of sassy come in handy and the strengths of SASS 
can really shine. In this example we have a three column grid, 
that will break into lines when the breakpoint is XS and smaller.

<Preview href="/examples/gridResponsive"/>

::: details CODE
```sass
.container
  +container

.grid
  +grid()

// Our item has 4 columns by default but has 12 columns on the breakpoint 
// XS and smaller
.item
  // Define the default state of your item
  +gridItem(4)
  
  +bpXsAndSmaller
    // Define the state if the item is rendered on breakpoint XS or smaller (XXS)
    +gridItem(12)
```

```html
<div class="container">
    <div class="grid">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
        <div class="item">5</div>
        <div class="item">6</div>
    </div>
</div>
```
:::

## Grid with vertical gutter
For the most of the daily layout work it is enough to have items with a horizontal gutter.
But sometimes you want a grid that handles the vertical gutter for you. The Sassy grid comes with
support for vertical gutter build in. If not configured different both the horizontal and vertical
gutter have the same size between elements.

To create a grid with vertical gutter simply use the gridV() and gridItemV() mixins instead of the default ones.
The result is a grid like the one below. Note how the grid automatically compensates for the vertical gutter of the 
first and the last row in your grid.

<Preview href="/examples/gridVerticalGutter"/>

::: details CODE
```sass
.container
  +container

.grid
  // We use gridV here to let the grid know that it should 
  // compensate for the vertical gutter
  +gridV()

.item
  // You need to define your items to have a vertical gutter by using 
  // the gridItemV mixin instead of the gridItem mixin. 
  // The options are identical for gridItemV and gridItem.
  +gridItemV(6)
  
  // This works for responsive grids as well
  +bpXsAndSmaller
    +gridItemV(12)
```

```html
<div class="container">
    <div class="grid">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="item">3</div>
        <div class="item">4</div>
    </div>
</div>
```
:::

## Grid Item Order
Sometimes you want to reorder the items in your grid depending on your breakpoint,
a filter or other means. In that case you can use the build in "order" feature 
that comes with flexbox and is integrated into sassy's grid system.

By default the first four items in any grid will be automatically defined
with the order value of 10, 20, 30 and 40. You can change the number of items
to automatically sort via the configuration. 

You can also manually apply an order while you define a grid item or by using
the gridItemOrder() mixin.

In the example below you will see that the items are in order 1,2,3 even
if they are defined in reverse in the HTML markup.

<Preview href="/examples/gridOrder" />

::: details CODE
```sass
.container
  +container

.grid
  +grid()

.item
  // By default the first four items will be automatically
  // ordered in every grid you create (you can change or
  // disable this via the configuration)
  +gridItem(4)

  &--first
    // You can set the order of an item using the gridItem() mixin...
    +gridItem(4, (order: 1))

  &--second
    // ... or you can use the gridItemOrder() mixin
    +gridItemOrder(2)
```

```html
<div class="container">
    <div class="grid">
        <div class="item">3</div>
        <div class="item item--second">2</div>
        <div class="item item--first">1</div>
    </div>
</div>
```
:::

## Grids with a custom number of column
Most of the grids out there in the interwebs are static; meaning you have a given number of columns in any grid you create on your page.
However sometimes your design contains 5 columns what to do about that. Sometimes you have a complete page that works with a three column layout,
wouldn't it be convenient to tell your grid you want 1 of 3 or 1 of 5 columns? The Sassy grid has you covered. 
Every item can be given the "of" option to tell it how many columns there are in a row. You can even mix and match them in a single grid.

<Preview href="/examples/gridCustomCols" />

::: details CODE
```sass
.container
  +container

.grid
  +grid()
  
// The 12 columns in a layout are configurable on a project level using the config options.
// However you can modify the number of expected columns in a row using the "of" option in your item
.item
  +gridItem(1, (of: 2))

.itemThird
  +gridItem(1, (of: 3))

.itemFifth
  +gridItem(1, (of: 5))
```

```html
<div class="container">
    <div class="grid">
        <div class="item">1</div>
        <div class="item">2</div>
        <div class="itemThird">3</div>
        <div class="itemThird">4</div>
        <div class="itemThird">5</div>
        <div class="itemFifth">6</div>
        <div class="itemFifth">7</div>
        <div class="itemFifth">8</div>
        <div class="itemFifth">9</div>
        <div class="itemFifth">10</div>
    </div>
</div>
```
:::

## Grid Item Offset
When you want an empty space between two grid items (horizontally) you can use offsets.
Offsets are defined as an option on your gridItem() mixin. You can add an offset before
an item (offset) or after an item (offsetAfter). The offset value is defined the same way as 
you define the span of your grid item.

<Preview href="/examples/gridOffset" :height="150"/>

::: details CODE
```sass
.container
  +container

.grid
  +grid()

.item
  +gridItem(4)
  
  &--offsetBefore
    +gridItem(4, (offset: 4))
  
  &--offsetAfter
    +gridItem(4, (offsetAfter: 2))
  
  &--wide
    +gridItem(6)
```

```html
	<div class="container">
		<div class="grid">
			<div class="item">1</div>
			<div class="item item--offsetBefore">2 (Offset before)</div>
			<div class="item item--offsetAfter">3 (Offset after)</div>
			<div class="item item--wide">4</div>
		</div>
	</div>
```
:::

## Gutter Configuration
In the sections above you already read about the "gutter". It is the space between items, horizontally and vertically (if you use the gridV mixin).
You can configure the default values for both types of gutter in the configuration. In addition to that
you also can override those defaults per grid item using the "gutter" option.

Take a look in the code example to see all the options you have to modify the gutter of an item

### Config for the default grid

<Preview href="/examples/gridGutterConfig" :height="130"/>

::: details CODE
```sass
.container
  +container

.grid
  +grid()

.item
  +gridItem(2)
  
  +bpSmAndSmaller
    +gridItem(4)
  
  // You can completely remove the gutter on both sides
  &--noGutter
    // "off" and "auto" are equivalent with setting the value to 0
    $opt: (gutter: false)
    +gridItem(2, $opt)
    
    +bpSmAndSmaller
      +gridItem(4, $opt)
  
  // Remove the gutter on the left side
  &--noGutterLeft
    // "auto" and "true" both are replaced with the default gutter 
	// set in the config
    $opt: (gutter: 0 auto)
    +gridItem(2, $opt)
    
    +bpSmAndSmaller
      +gridItem(4, $opt)
  
  // Remove the gutter on the right side
  &--noGutterRight
    $opt: (gutter: auto 0)
    +gridItem(2, $opt)
    
    +bpSmAndSmaller
      +gridItem(4, $opt)
  
  // You can also modify the value instead of disabling it
  // NOTE: The gutter definition will be split by 2 because the gutter 
  // is always shared between two items.
  &--changedGutter
    $opt: (gutter: (left: 60px, right: 10px))
    +gridItem(2, $opt)
    
    +bpSmAndSmaller
      // You can also define different gutters on different breakpoints
      $opt: (gutter: (left: off, right: 10px))
      +gridItem(4, $opt)
```

```html
	<div class="container">
		<div class="grid">
			<div class="item item--noGutterLeft">No gutter left</div>
			<div class="item item--noGutter">No gutter</div>
			<div class="item item--changedGutter">Custom gutter</div>
			<div class="item item--noGutterRight">No gutter right</div>
			<div class="item item--noGutterLeft">No gutter left, too</div>
			<div class="item item--noGutterRight">No gutter right, too</div>
		</div>
	</div>
```
:::

### Config for the grid with vertical gutter

<Preview href="/examples/gridGutterConfig/indexv.html" />

::: details CODE
```sass
.container
  +container

.gridV
    // You can change the gutter compensation using any 
	// valid gutter definition. Here we disable the vertical compensation 
	// but leave the horizontal value on the default
    +gridV(0 auto)
    
.itemV
  +gridItemV(4)

  &--noGutter
    // You can set "true" to use the default gutter on all sides or 
	// "false" to disable the gutter on all sides
    +gridItemV(4, (gutter: false))

  &--noGutterVertical
    // You can use the css short syntax like "vertical gutter" and 
	// "horizontal gutter"
    +gridItemV(4, (gutter: 0 true))

  &--noGutterHorizontal
    +gridItemV(4, (gutter: auto 0))

  &--noGutterLeft
    // You can use the sass map syntax for "top", "right", "bottom" and "left"
    +gridItemV(4, (gutter: (left: false)))

  &--noGutterRight
    // You can also use the css syntax for "top", "right", "bottom" and "left"
    +gridItemV(4, (gutter: auto 0 auto auto))
```

```html
	<div class="container">
		<div class="grid">
			<div class="item item--noGutterLeft">No gutter left</div>
			<div class="item item--noGutter">No gutter</div>
			<div class="item item--changedGutter">Custom gutter</div>
			<div class="item item--noGutterRight">No gutter right</div>
			<div class="item item--noGutterLeft">No gutter left, too</div>
			<div class="item item--noGutterRight">No gutter right, too</div>
		</div>
	</div>
```
:::