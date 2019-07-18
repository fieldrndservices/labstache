# Mustache: A LabVIEW&trade; Toolkit for Rendering Logic-Free Mustache Templates 

[About](#what-is-mustache-lv) | [Installation](#installation) | [Documentation](#documentation) | [Tests](#tests) | [License](#license)

## What is Mustache for LabVIEW?

Mustache-LV is a pure LabVIEW library for working with logic-free [mustache](https://mustache.github.io/) templates. Logic-less Mustache templates are a simple template design that works great with any text-based file, especially formats that use a markup language, i.e. HTML. This library enables [LabVIEW](https://www.ni.com/labview) developers to interact with and use Mustache templates.

## Installation

A VI Package (VIP) is available on the [National Instruments (NI)](http://www.ni.com) [LabVIEW Tools Network](http://www.ni.com/labview-tools-network/). It is recommended to use the [VI Package Manager](https://vipm.jki.net/) published by [JKI](http://jki.net/) to install and update the library.

## Documentation

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed, or visit the [web-based documentation](https://help.fieldrndservices.com/mustache-lv). Examples are also available within the LabVIEW development environment using the `Help->Find Examples...` menu item.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the `Tests` project library (.lvlib) and the `tests` on-disk folder. To run the tests, open the `Mustache.lvproj` file found in the root folder of the source code distribution in the LabVIEW Development Environment (32-bit or 64-bit) and run the `Run All` VI that is found in the `Tests` project library. The tests are organized in a hierarchy based on their relationship to the source code. There is a `Run All` VI within each child project library (.lvlib) to run all of the tests for a specific portion of the project.

## License

See the `docs` folder for all information about licensing and copyright.

