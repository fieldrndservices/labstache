# Field R&D Services: Labstache Change Log

All notable changes to this project will be documented in this file, which is written in plain text (ASCII) using the [Markdown](http://daringfireball.net/projects/markdown/syntax) lightweight markup language. This project adheres to [Semantic Versioning](http://semver.org). 

## [Unreleased][Unreleased]

## [1.1.0] - 2019-10-04

### Added

- Some tests for the Data project library VIs and Classes
- Some tests for recursive partials

### Changed

- Partial loading to the rendering stage
- Parsing partials to the rendering stage
- Input and output descriptions to be consistent

### Fixed

- Recursive partials causing an infinite loop
- Data stack searching from the bottom instead of the top

## [1.0.1] - 2019-08-13

### Added

- Input and output descriptions to VI descriptions

### Fixed

- Controls and indicators descriptions to be more consistent in formatting and wording

## [1.0.0] - 2019-08-05

### Added

- High-level Compile VI
- High-level Data VIs to create Mustache data values and types from LabVIEW primitives
- Low-level rendering of an abstract syntax tree to a string based on provided data values and types
- Low-level parsing of tokens into an abstract syntax tree
- Low-level Lexer class
- Tests
- Examples
- VI documentation
- Class documentation
- Project library documentation
- HTML Help documentation
- Scripts for building and packaging toolkit
- Script for generating HTML help documentation from VIs, Classes, and project libraries
- License file
- On-disk project organization
- LabVIEW project file

