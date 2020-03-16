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

## Documentation
The documentation can be found [here](https://sassy.neunerlei.eu/).

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
