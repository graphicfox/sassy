# Margins, Paddings & Spacer
In most of the projects I'm working on there is a consistent design system, meaning that margins and paddings are always following a ruleset.
Your margins are either 15px or 30px or 45px. Your paddings are 5px or 10px or 15px and so on. 
Thats where the margin and padding mixins are used. 

They are designed to work with a system where you have spacings that are always a multitude of a given value.
Therefore you can simply configure the global, default margin and then tell the mixin: "hey give me 2 times the default value".

## Values
As stated above you can pass any numeric value to the following mixins.
If the value **has a unit** (like px or %) it will simply be passed to the matching property.
if the value **does not have a unit** it will be used as a multiplier for the default $margin value.
If you don't pass any value into the mixin we assume you just want to put the default value there

::: tip 
Both ```$sassyMargin``` and ```$sassyMargin``` can be overwritten by the "horizontal" and "vertical" options if you want 
another margin horizontally than you want vertically.
:::

## Margins
You can use the margin mixins in the same logic you would use in your default css.
All those mixins depend on the configured ```$sassyMargin``` value. By default the ```$sassyMargin``` is set to 15px
```sass
.element
    +m() // Set the margin on all sides
    +mt() // Margin top
    +mr() // Margin right
    +mb() // Margin bottom
    +ml() // Margin left
    +mh() // Horizontal Margin (left and right)
    +mv() // Vertical Margin (top and bottom)
```

## Paddings
Paddings work similar to margins but have **one major difference**: By default all paddings depend
on the configured ```$sassyPadding``` option. This option is by default a thrid of the ```$sassyMargin``` value.
So with the default ```$sassyMargin``` of 15 px the ```$sassyPadding``` will be set to 5px.

```sass
.element
    +p() // Set the padding on all sides
    +pt() // Padding top
    +pr() // Padding right
    +pb() // Padding bottom
    +pl() // Padding left
    +ph() // Horizontal Padding (left and right)
    +pv() // Vertical Padding (top and bottom)
```

## Spacers
Spacers or space between elements are a recurring theme in most designs. 
Sassy's spacers are designed to keep spacer elements based on your design system.
For that you have a ```$sassySpacerBase``` base value (set to ```$sassyMargin``` by default) that
will be multiplied by a given multiplier. 

To keep all spacers equal sassy works with a list of configurable multipliers (```$sassySpacerMultipliers```).
The default list is: 2, 4, 6 and 8. When you define a spacer you can simply pass the id of your spacer (1-4) in a mixin
and the multiplication will automatically be applied. 

If you pass a value that exceeds the list of predefined spacers it will be applied as multiplier instead.
(e.g. if you pass 6 or 7 it exceeds the default list of 4 and therefore the spacer) will be $sassySpacerBase * 6 or 7.

```sass
.element
    +st() // Spacer to the top
    +sb() // Spacer to the bottom
```