# Changelog
All notable changes to this project will be documented in this file.

## [Unreleased]
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
