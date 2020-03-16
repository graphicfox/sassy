# Sassy

Sassy is a lightweight package to create responsive websites with ease. I personally worked with bootstrap for a couple of years but it was always somewhat cumbersome as it did not match the BEM doctrine I use for my projects, it was too static for my liking when you have edge cases and brings a lot of stuff I never used. 

This package is the distilled down sum of features I wanted from bootstrap and it's competitors but without adding a single css class on its own.
It just brings you a bundle of mixins you can use in your SASS or SCSS code to create grids, handle breakpoints and create consistent margins / paddings over your page.

The bundle is written completely in SASS (not SCSS) and is designed to work in a SASS/SCSS project. If you are looking for a drop in solution for your (existing) CSS this is probably not the package for you.

## Installation
The installation of sassy is quite simple, just pull it strait from npm:

```
npm install --save @neunerlei/sassy
```

## Usage
After you installed sassy in your dependencies you can add it in your sass file like:
```sass
// [optional] Sassy comes with it's own css reset which is based 
// on necolas/normalize.css with some adjustments
// and additional rules. Use it like
@import "~@neunerlei/sassy/Components/CssReset"

// Load the sassy mixins and the default configuration
@import "~@neunerlei/sassy/Resources"
@import "~@neunerlei/sassy/Config"
```

## Usage with LABOR Asset-Building
If you are using the LABOR asset-building package you have the option to use the [superscript resource loader](https://github.com/labor-digital/asset-building#css-superscript-resources).
It provides all your sass files with a common "Resources.sass" you have in your project root. Sassy is designed with that resource loader in mind.

In your "Resources.sass" file add just the resources definition: 
```sass
// [optional] Add your custom config to the Resources.sass as well!
@import "./path/to/config"

// Import the resources and the configuration like normal.
@import "~@neunerlei/sassy/Resources"
@import "~@neunerlei/sassy/Config"
```

After that you can use sassy in your project file. If you want to use the breakpoint service or the css reset simply add them to your style root file.
```sass
// [optional] Add Sassy css reset
@import "~@neunerlei/sassy/Components/CssReset"
// [optional] Add Sassy breakpoint service
@import "~@neunerlei/sassy/Components/BreakpointService"
```

## Source Code
The source code can be found on [github](https://github.com/Neunerlei/sassy).

## Building the documentation
The documentation is powered by [vuepress](https://vuepress.vuejs.org/), you can quite simply spin up a dev server like so:

- Clone the repository
- Navigate to ```docs```
- Install the dependencies with ```npm install```
- Run the watcher for the examples with ```npm run devDemos```
- In another console window, run the dev server with ```npm run dev```

## Special Thanks
Special thanks goes to the folks at [LABOR.digital](https://labor.digital/) (which is the german word for laboratory and not the english "work" :D) for making it possible to publish my code online.

## Postcardware
You're free to use this package, but if it makes it to your production environment I highly appreciate you sending me a postcard from your hometown, mentioning which of our package(s) you are using.

You can find my address [here](https://www.neunerlei.eu/). 

Thank you :D 
