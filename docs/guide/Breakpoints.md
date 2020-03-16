# Breakpoints
Breakpoints are an integral part of responsive webdesign. You know them from bootstrap or other, similar libraries. 
They are basically fixed widths of your browser window from which your design should "break" to another layout to fit the new resolution. 
Normally you would use [media queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp) to check if your screen is wider or narrower than a given pixel value.

I worked with bootstrap over the course of years so it is probably not surprising that the sassy breakpoints wil look familiar for you. 

In general you have 6 breakpoints as a default XXS - XL
The size of each breakpoint can be configured using the config options.

## Default breakpoints
The default breakpoint widths are:
- XXS: 0px   - 300px
- XS:  0px   - 449px
- SM:  550px - 767px
- MD:  768px - 991px
- LG:  992px - 1199px
- XL:  >= 1200px

## XS and XXS
By default the XS and the XXS breakpoints are fluid. This means that a query on breakpoint XS
returns true even if you are actually in breakpoint XXS. With this design choice you CAN use the XXS breakpoint
for special edge cases but can use XS without any issues if you don't need fine controls

## Breakpoint queries
For each breakpoint there are multiple mixins you may use, here is an example for the MD breakpoint,
but you have the equivalents for each of the breakpoints listed above:

- +bpSmallerThanMd -> window width < 768px
- +bpMdAndSmaller -> window width <= 991px
- +bpMd -> window width >= 768px && <= 991px
- +bpMdAndBigger -> window width >= 768px
- +bpBiggerThanMd -> window width > 991px

*NOTE: For the breakpoint XXS there is no bpSmallerThanXxs and no bpXxsAndSmaller because there is
nothing you could compare for. For the breakpoint there is no bpXlAndBigger and no bpBiggerThanXs for the same reason.*

## Custom queries
In addition to the default breakpoints sassy comes with additional mixins for defining media queries with custom values.
The mixins you can use with your own width's are:

- +bpSmallerThan($width) -> window width <= $width
- +bpBiggerThan($width) -> window width >= $width
- +bpBetween($widthA, $widthB) -> window width >= $widthA && <= $widthB

## Example
You should probably open this example in a new tab to see it in action.

<Preview href="/examples/breakpoints" />

::: details CODE
##### SASS
```sass
.breakpointOutput:after
  +ml(5px)
  content: "XS"
  +bpXxs
    content: "XXS"
  +bpSm
    content: "SM"
  +bpMd
    content: "MD"
  +bpLg
    content: "LG"
  +bpXl
    content: "XL"
```

##### HTML
```html
<div class="container">
    <div class="breakpointOutput">
        Breakpoint: 
    </div>
</div>
```
:::

## Breakpoint Service
Have you ever wanted to listen to breakpoint changes in your Javascript? Then you know that you have
to duplicate the definition of your breakpoints both in your CSS and your JS. This is where 
the breakpoint service comes in. It provides a css class that contains the information about your
current breakpoint configuration. This class can be parsed by your javascript automatically. 
Therefore you don't have to configure the breakpoints twice.

The generated class will look similar than the following example. As you can see,
the breakpoints are transferred as font-family that the javascript implementation can parse.
```css
.sassy-breakpoint-service {
    font-family: "xxs: 0|449px, xs: 0|549px, sm: 550px|767px, md: 768px|991px, lg: 992px|1199px, xl: 1200px|999999px";
}
```

Currently the [@labor/helferlein](https://www.npmjs.com/package/@labor-digital/helferlein) package contains a implementation called [BreakpointService](http://helferlein.labor.tools/classes/_ui_breakpointservice_breakpointservice_.breakpointservice.html) that works out of the box with Sassy.

::: info 
The helferlein bundle is a temporary solution. I'm working on splitting it up into smaller, more focused bundles where the breakpoint service will have a separate package.
:: 

Your javascript/typescript would look like:
```typescript
import {BreakpointService} 
    from "@labor/helferlein/lib/Ui/BreakpointService/BreakpointService";

BreakpointService.bpIs(">=", "sm");
```