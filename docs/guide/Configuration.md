# Configuration
You can configure every aspect of the Sassy library to match the needs of your project. Sassy
comes with it's own configuration file that uses sass' "!default" modifier that will only set a variable if it is not already defined.
So its easy to override single values without copying the whole config file.

## Adding your configuration
To create your own, project specific configuration just create a new sass file (e.g. config.sass) and 
include it before you include the "Config.sass" that comes with sassy.

```sass
// Load your own configuration
@import "./path/to/config"

// Load the sassy mixins and the default configuration
@import "~@neunerlei/sassy/Resources"
@import "~@neunerlei/sassy/Config"
```

So in this example we modified the width's of the breakpoints. The source code
of this example is identical with [this one](./breakpoints.md#example)
```sass
$sassyBreakpointSmMin: 350px
$sassyBreakpointMdMin: 400px
$sassyBreakpointLgMin: 450px
$sassyBreakpointXlMin: 500px
```

An now get this result instead of the default breakpoints

<Preview href="/examples/configuration" />

## Breakpoints
The first part of the configuration defines the breakpoints. They have the following default values:
```sass
// Min sizes
$sassyBreakpointXxsMin: 0 !default
$sassyBreakpointXsMin: 0 !default
$sassyBreakpointSmMin: 550px !default
$sassyBreakpointMdMin: 768px !default
$sassyBreakpointLgMin: 992px !default
$sassyBreakpointXlMin: 1200px !default

// Max sizes
$sassyBreakpointXxsMax: 300px !default
$sassyBreakpointXsMax: $sassyBreakpointSmMin - 1px !default
$sassyBreakpointSmMax: $sassyBreakpointMdMin - 1px !default
$sassyBreakpointMdMax: $sassyBreakpointLgMin - 1px !default
$sassyBreakpointLgMax: $sassyBreakpointXlMin - 1px !default
$sassyBreakpointXlMax: 999999px !default

// Service definition
// The name of the class that provides the breakpoint definition to the js counterpart
$sassyBreakpointServiceClass: sassy-breakpoint-service !default
```

## Grids
You can also configure all aspects of grids including the size of the container on each breakpoint:
```sass
// The number of columns used in the grid by default
// You can override this by using "of" in your gridItem options
$sassyGridColumns: 12 !default
// True to automatically create the flex-box order
$sassyAutoOrder: true !default
// The number of elements which get their order automatically set
$sassyAutoOrderLength: 4 !default
// The gutter for both the horizontal and vertical axis
// You can override this by using "offset" in your gridItem options
$sassyGutter: 30px !default
$sg: $sassyGutter !default // shortcut!
// Optional override to change the vertical
$sassyGutterVertical: $sassyGutter !default
$sgv: $sassyGutterVertical !default // shortcut!
$sassyGutterHorizontal: $sassyGutter !default
$sgh: $sassyGutterHorizontal !default // shortcut!

// Container sizes for the different breakpoints
$sassyContainerWidthXxs: 100% !default
$sassyContainerWidthXs: 100% !default
$sassyContainerWidthSm: 550px !default
$sassyContainerWidthMd: 720px !default
$sassyContainerWidthLg: 960px !default
$sassyContainerWidthXl: 1140px !default
```

## Margins, Paddings & Spacer
The last part of the configuration is to define the sizes for margins and paddings:
```sass
// MARGINS
// ==================================================
$sassyMargin: 15px !default
$margin: $sassyMargin !default // shortcut!
$sassyMarginHorizontal: $sassyMargin !default
$sassyMarginVertical: $sassyMargin !default

// PADDINGS
// ==================================================
$sassyPadding: $sassyMargin / 3 !default
$sassyPaddingHorizontal: $sassyMarginHorizontal / 3 !default
$sassyPaddingVertical: $sassyMarginVertical / 3 !default

// SPACERS
// ==================================================
$sassySpacerBase: $sassyMargin !default
$sassySpacerMultipliers: 2 4 6 8 !default
```