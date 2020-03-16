# Changelog

All notable changes to this project will be documented in this file. See [standard-version](https://github.com/conventional-changelog/standard-version) for commit guidelines.

### [2.0.2](https://github.com/Neunerlei/sassy/compare/v2.0.1...v2.0.2) (2020-03-16)

### [2.0.1](https://github.com/Neunerlei/sassy/compare/v2.0.0...v2.0.1) (2020-03-16)

## [2.0.0](https://github.com/Neunerlei/sassy/compare/v1.1.0...v2.0.0) (2020-03-16)


### ⚠ BREAKING CHANGES

* the grid syntax was changed in comparison with earlier
versions. Therefore this version will break existing projects that use
the grid mixins

### Features

* add some minor new features + fix issue with gird item ordering ([e364cb1](https://github.com/Neunerlei/sassy/commit/e364cb15c4f9411e4dcfe9adbf084dcd4036fc8f))
* consolidation + documentation before publishing the package ([3431eff](https://github.com/Neunerlei/sassy/commit/3431eff5ce41300a3bd3d344ea39f7731db1034f))

# [1.1.0](https://bitbucket.org/labor-digital/labor-sass-sassy/branches/compare/v1.1.0%0Dv1.0.2#diff) (2019-03-27)


### Bug Fixes

* fix proportionalContainer padding-top miscalculation ([9ae88de](https://bitbucket.org/labor-digital/labor-sass-sassy/commits/9ae88de))
* fix that $margin is no longer the half of $sassyMargin ([d25b554](https://bitbucket.org/labor-digital/labor-sass-sassy/commits/d25b554))


### Features

* a, button, input[type=submit] are now inline elements by default ([de3428a](https://bitbucket.org/labor-digital/labor-sass-sassy/commits/de3428a))



## [1.0.2] - 2019-01-11
### Added
- Added fallback when spacers are used out of their configured multiplier bounds
- Added "auto" value for grid gutter definitions
- Added "offset" option to gridItem()

### Changed
- Makes headline elements "display: block" again in the cssReset
- Added p tags to the list of "display: inline-block" elements in the cssReset
- Changed grid container to render a gutter left and right if the width is 100%
- Grid items can now be set to "off" to disable the handling as flex element

### Fixed
- Fixed an issue with the grid item order 
- Makes sure that all grid values will be calculated as pixels to prevent errors

## [1.0.1] - 2019-01-10
### Added
- Added mixins for padding and margin
- Added some misc helpers from bootstrap-addons
- Added flex mixins
- Added spacer mixins

### Changed
- Makes css class for the breakpoint bridge configurable
- Renamed breakpointBridge to BreakpointService

## [1.0.0] - 2018-12-20
Initial commit


The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).
