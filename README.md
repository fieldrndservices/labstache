# Labstache: A LabVIEW&trade; Toolkit for Rendering Logic-Free Mustache Templates 

Labstache is a pure [LabVIEW](http://www.ni.com/labview) library for working with logic-free [Mustache](https://mustache.github.io/) templates. Logic-less Mustache templates are a simple format using curly bracket delimiters (`{{}}`) that works great with any text-based file, especially formats that use a markup language, such as HTML. This library enables LabVIEW developers to interact with and use Mustache templates.

## Table of Contents

- [Example Usage](#example-usage)
- [Dependencies](#dependencies)
  - [Installation](#dependencies-installation)
  - [Development](#dependencies-development)
- [Installation](#installation)
- [Build](#build)
  - [Packaging using VIPM Pro (recommended)](#packaging-using-vipm-pro-recommended)
  - [Packaging using VIPM Free](#packaging-using-vipm-free)
- [Documentation](#documentation)
- [Tests](#tests)
- [License](#license)

## Example Usage

A [VI snippet](http://www.ni.com/tutorial/9330/en/) of compiling, or rendering, a mustache template as a string into a string:

![Simple Mustache String Rendering](https://github.com/fieldrndservices/labstache/blob/master/docs/Simple-Mustache-String-Rendering.png)

A VI snippet of compiling, or rendering, a mustache template from a file to another file:

![Simple Mustache File Rendering](https://github.com/fieldrndservices/labstache/blob/master/docs/Simple-Mustache-File-Rendering.png)

## Dependencies

### Installation <a name="dependencies-installation"/>

- LabVIEW 2009 or newer (All systems)

### Development <a name="dependencies-development"/>

- [Caraya](http://sine.ni.com/nips/cds/view/p/lang/en/nid/215909)
- [HTML Help Workshop](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/htmlhelp/microsoft-html-help-downloads) (for compiling the help documentation)
- [JKI State Machine](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209025)
- LabVIEW 2009 or newer (for building)
- LabVIEW 2018 or newer
- Labricator (only for automated builds, private package available upon request)
- [OpenG Array Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [OpenG File Library](http://sine.ni.com/nips/cds/view/p/lang/en/nid/209027)
- [VIPM Pro](https://vipm.jki.net/get) (only for automated builds)
- [VIPM API](https://support.jki.net/hc/en-us/articles/214136183-VIPM-API) (only for automated builds)

The Caraya, JKI State Machine, OpenG Array Library, OpenG File Library, and VIPM API dependencies must be installed for all versions of LabVIEW (2009 and 2018) to avoid errors during automated builds.

## Installation

A VI Package (VIP) will (hopefully) be available on the [National Instruments (NI)](http://www.ni.com) [NI Tools Network](http://www.ni.com/labview-tools-network/) in the future. It will be recommended to use the [VI Package Manager](https://vipm.jki.net/) published by [JKI](http://jki.net/) to install and update the library once it is available. Until then, the library can only be installed by: (i) downloading the source code and building the VIP, (ii) downloading a VIP from the [releases](https://github.com/fieldrndservices/libssh2-labview/releases) section of this project, (iii) manually copying the VIs from the source code into a project, or (iv) requesting a VIP from the authors.

## Build

Each component in the Labstache project has a Source Distribution build specification. The destination of each source distribution build is the `builds` folder relative to the project root, i.e. same folder as the `Labstache.lvproj` file. Additionally, the output for the compiled help documentation is also the `builds` folder. The `builds` folder should _not_ be included in the version control repository. A `Build.vi` script is available in the `Scripts.lvlib` project library that will build all of the components and the help documentation automatically (VIPM Pro is not needed, but the [HTML Help Workshop](https://docs.microsoft.com/en-us/previous-versions/windows/desktop/htmlhelp/microsoft-html-help-downloads) is needed).

The VI Package Build (.vipb) specification, located in the `configs` folder relative to the project root, is configured for the package source to be the `builds` folder. Thus, the Source Distribution for each component must be built **before** opening the `Labstache.vipb` file in the <abbr title="VI Package Manager">VIPM</abbr>; otherwise, the package configuration will be lost.

### Packaging using VIPM Pro (recommended)

__Important__, if creating a package for LabVIEW 2009 from LabVIEW 2018, the [VI Server TCP/IP ports](http://zone.ni.com/reference/en-XX/help/371361P-01/lvhowto/configuring_the_vi_server/) must be different for each version of LabVIEW and verified with the [VIPM](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z000000P9YmSAK) application _before_ proceeding. An error will occur when the VIPM is started if both LabVIEW 2009 and 2018 are running at the same time. Basically, VIPM will not know which VI server to use if both versions of LabVIEW are using the same TCP/IP port.

If VIPM Pro is available, then open the `Labstache.lvproj` file in any version of LabVIEW newer than 2009 and run the `Package.vi` located in the `Scripts.lvlib` project library of the Project Explorer window. Ensure all dependencies are installed before running the `Package.vi` script.

Note, the version number for the package is set in the `configs\Labstache.vipb` file. The version number in the VIP build specification file should be modified and saved _before_ running the `Package.vi` script.

### Packaging using VIPM Free

If VIPM Pro is _not_ available, then the following steps can be executed to do essentially the same thing as the `Package.vi` script. Ensure all dependencies, except VIPM Pro and the VIPM API, are installed before completing these steps.

1. Start LabVIEW 2018 or newer and open the `Labstache.lvproj` file.
2. From the Project Explorer window, **File>>Save for Previous Version...**, a new dialog will appear.
3. Select **9.0** from the drop down menu.
4. Click **Save...**. A new dialog will open.
5. Create the `target\9.0` folder hierarchy in the project root, i.e. the same folder as the `Labstache.lvproj` file, if it does not already exists.
6. Click **Save**.
7. Close LabVIEW 2018 or newer and the `Labstache.lvproj` file.
8. Navigate to `<project root>\src`.
9. Copy the `Help` folder to `<project root>\target\9.0\src`.
10. Start LabVIEW 2009.
11. Open the `<project root>\target\9.0\Labstache.lvproj` file. Do NOT open the project in any other version of LabVIEW.
12. Open each Source Distribution build specification under the "Build Specifications" tree item in the Project Explorer and change the _Output Destination_ to `<project root>\target\9.0\builds`. Save and close each build specification.
13. Run the `Build.vi` in the `Scripts` project library to build each Source Distribution under the "Build Specifications" tree item and the compiled help documentation file (`Labstache.chm`). The output of each build will be available in `<project root>\target\9.0\builds`.
14. Open the `<project root>\target\9.0\configs\Labstache.vipb` file in VIPM.
15. Build the VI package with VIPM. The output will be available at `<project root>\target\9.0\packages`. Do NOT modify anything in the package build specification, but ensure the "2009" version of LabVIEW is selected in the upper, right-hand corner of the VIPM application window.
16. Close VIPM.
17. Close LabVIEW 2009 and the `<project root>\target\9.0\Labstache.lvproj` file.

## Documentation

See the in-app LabVIEW Help system for more information and documentation about using the library after it has been installed, or (eventually) visit the [web-based documentation](https://help.fieldrndservices.com/labstache). Examples are also available within the LabVIEW development environment using the "Help->Find Examples..." menu item.

## Tests

Tests are written in LabVIEW using the [Caraya](https://github.com/JKISoftware/Caraya) unit testing framework and included in the project via the various `Tests.lvlib` project libraries and the `tests` on-disk folder. To run the tests, open the `Labstache.lvproj` file found in the project root in the LabVIEW Development Environment and run the `Test.vi` script located in the `Scripts.lvlib` project library. This will run all of the tests defined in all of the various `Tests.lvlib` project libraries located in the project. 

## License

Labstache is licensed under the [MIT](https://opensource.org/licenses/MIT) license. See the `docs` folder for all information about licensing and copyright.

