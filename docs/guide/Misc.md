# Miscellaneous 
Sassy comes with some additional features to make your live easier.

## CSS Reset
[Normalize.css](https://github.com/necolas/normalize.css) is my browser reset for years as it is a really good starting point.
I added some additional rules based on our companies old reset and converted the .css file to sass.
All credit goes to the initial author!

Different behaviour in the sassy version of normalize.css:

- all fonts and headlines are reset to a unified size and have their margin removed
- all buttons have their styles removed
- all elements are set to: box-sizing: border-box
- all a, button, span, p, fieldset and legend tags are set to display: inline-block

## Mixins
#### transition($duration: 0.5s, $what: all, $easing: linear)
A simple helper for handling css transitions

#### imageBg($bgImage: null, $type: cover)
Adds either the a background image to the element
or if $bgImage is not given only provides the common background image configuration for an element

#### proportionalContainer($width, $height)
Creates a container that has always a fixed size ratio
even when the outer container is scaled based on the width

#### printOnly()
Renders it's content only when printed and not on a screen

#### screenOnly()
Renders it's content only on a screen and not in the print mode

#### flexCenterH()
Centers the children of the element horizontally using flexbox

#### flexCenterV()
Centers the children of the element vertically using flexbox

#### flexCenter()
Centers the children of the element on both axis using flexbox