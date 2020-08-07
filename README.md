# Markers4Map
[Markers4Map](https://niebert.gihub.io/Markers4Map) is an OpenSource tool developed for creating markers/icons with a info popup for the tagged geolocation on a map. The map is generated with [OpenLayers](https://www.openlayers.org) and the mapping source [OpenStreetMap](https://www.openstreetmap.org).

* **[Markers4Map Demo](https://niebert.github.io/Markers4Map)**

The data for the markers, popups for the geolocation are stored in a JSON file and shared with others. Stored JSON data can be loaded from the WebApp [Markers4Map](https://niebert.github.io/Markers4Map).

The information about the markers/icons/popups is stored in link/url that can be used e.g. Wikiversity for a specific learning resource.

The documentation for [Markers4Map](https://niebert.github.io/Markers4Map) is available in [Wikiversity-Markers4Map](https:/en.wikiversity.org/wiki/Markers4Map).

The WebApp [Markers4Map](https://niebert.github.io/Markers4Map) is a [AppLSAC](https://en.wikiversity.org/wiki/AppLSAC) with privacy friendly data management in the browser in mind.

Display of the markers is performend with the following package:
* [openlayer_display_markers](https://www.github.com/niebert/openlayer_display_markers) URL: https://www.github.com/niebert/openlayer_display_markers
* Similar repository to [Mapper4SDG](https://www.github.com/niebert/Mapper4SDG) for mapping activities for [Sustainable Development Goals](https://en.wikiversity.org/wiki/Sustainable_Development_Goals) on map.


## Online Demo

* https://niebert.github.io/Markers4Map

## JSON Data
The JSON data has the following structure.
```javascript
vDataJSON["initdata"] = [
    {
        "id": "2821",
        "lat": "51.493889053694915",
        "lng": "-0.14467470703124907",
        "title": "London",
        "summary": "London created a Open Innovation Ecosystem for SDG Clean Water and Sanitation",
        "has_detail_page": "1",
        "webpage": "https://en.wikipedia.org/wiki/London",
    },
    {
        "id": "1508460902844",
        "lat": "51.243141",
        "lng": "-1.81185",
        "title": "Brimingham",
        "summary": "Birmingham created SDG-activities about SDG7 Clean and affordable Energy and SDG3 Health",
        "has_detail_page": "1",
        "webpage": "https://en.wikipedia.org/wiki/Birmingham",
    }
]
```
The init data is defined in `docs/db/data.js` in a Javascript file, so that the data can be loaded with a default `script`-tag.

## Load and Save data
You can load and save data in the WebApp with the `Load` and `Save`. Saving the current work on the local harddrive as JSON file is always recommended because the processing of data is not stored on a server. Data is kept in the browser and is saved in the LocalStorage of the browser (see https://en.wikiversity.org/wiki/AppLSAC)

## Browserify and Watchify
Browserify and Watchify are used in this repository to control the WebApp-javascript development with the required Javascript libraries installed with [NPM Node.js](https://docs.npmjs.com/getting-started/installing-node) and similar framework world that greatly improve your javascript workflow: Using them, you no longer need to micro-manage your script tags but instead you just declare the libraries each of your client-side modules is using - or you can even create your own reusable modules! Also, installing (or updating) javascript libraries is as easy as running a single command!
* [Additional Information about Browserify and Watchify on GitHub](https://spapas.github.io/2015/05/27/using-browserify-watchify/)
* [Youtube Video about Browserify and Watchify by Kyle Robinson Young 2015/04/16](https://www.youtube.com/watch?v=CTAa8IcQh1U)
In this repository Browserify and Watchify are used for javascript code development with [NPM Node.js](https://docs.npmjs.com/getting-started/installing-node).

### Global Installation of Browserify, Watchify, UglifyJS and DocToc
Requirement: [NPM](https://docs.npmjs.com/getting-started/installing-node) is intalled. Now call for global installation of Browserfy, Watchify, UglifyJS and DocToc by:

`npm install -g browserify watchify uglify-js doctoc`

This is recommended because your will not install Browserfy, Watchify and UglifyJS for all your repositories separately.
* ***Browserfy*** converts `node_modules` in a single library, that can be imported in WebApp. Browserify resolves dependencies and included the required libraries into the bundled javascript code.
* ***Watchify*** watches changes in the source code and runs the build process whenever it detects changes in the your source code.
* ***UglifyJS*** compresses the source code of ```class_editor_uml.js``` into ```class_editor_uml.min.js``` to reduce download time and WebApp performance during load.
* ***DocToc*** is used to create a helpful table of contents in the README (see [DocToc-Installation]https://github.com/thlorenz/doctoc#installation) for further details on [NPM DocToc](https://www.npmjs.com/package/doctoc) ). Run `doctoc README.md` for updating the table of contents.
* ***jsLint*** is used to check the Javascript code, quality of code can be improved by application of jsLint

### Package Installation of Browserify and Watchify - Alternative
If your prefer that  browserify and watchify is installed with your `npm install` command, save these to modules to your dev-dependecies in your `package.json` by calling

* (Install Browsersify) `npm install browserify --save-dev`
* (Install Watchify) `npm install watchify --save-dev`
* (Install UglifyJS) `npm install uglify-js --save-dev`
* (Install DocToc) `npm install doctoc --save-dev`
* (Install jslint) `npm install node-lint --save-dev`

The difference between `--save` and `--save-dev` is, that development dependencies are installed with `npm install` because they are required for the development process of the code but they are not added to the generated Javascript-bundle that are used in the WebApp ClassEditorUML. The `--save-dev` commands for `browserify` and `watchify` will install the two modules with all the the dependencies in `node_modules` and add the dev-dependencies to your `package.json`.
```json
"devDependencies": {
  "browserify": "^14.5.0",
  "watchify": "^3.9.0",
  "uglify-js": "^2.6.2",
  "doctoc":"^1.3.0",
  "lint": "^1.1.2"  
}
```
In the current repository `Browserfy` and `Watchify` are expected to be installed globally, because the `package.json` does not contain the dev-dependencies mentioned above.

### Start Watching the Files with Watchify
Watchify will trigger the `npm run build` process if files were change due to alteration of code. To start watching the files, run the npm-watch script by `npm run watch`, which is defined in `package.json`

## Source JS file and development bundle output

The main JS source file for the build process is `src/main.js`. The ouput library (resp. output file of build process) is stored in distrubtion library for browser based web-development in `dist/bundle.js`. Compressed code is generated with `UglifyJS`. It takes the `dist/bundle.js` as input file and creates the compressed file `dist/bundle.min.js`.

In this case the file `bundle.js` is `markers4map.js` and `bundle.min.js` is `markers4map.min.js`.


## Main Library for Handling the JSON Database

Main library to handle large arrays is `docs/js/editor4json.js`
https://github.com/niebert/Markers4Map/tree/master/docs

## UML Diagram of Editor4JSON Class

![UML Diagram of JS Class Editor4JSON](https://niebert.github.io/Markers4Map/Editor4JSON_UML.png)

## JSON Data and Schema

### Default JSON Data

Default JSON data is defined in `docs/db/data.json`. If data is changes the alterations are stored in the LocalStorage locally in the browser.

### JSON SCHEMA
The structure of the collected JSON data is defined by the JSON schema. The schema is defined in `docs/schema/mapobject.schema`. The schema for data collection can be defined by a [JSON2Schema Generator](https://niebert.github.io/json-editor/plugins/json2schema.html).  Defined an example of a JSON record for a single collected item and create with appropriate JSON schema with the [JSON2Schema Generator](https://niebert.github.io/json-editor/plugins/json2schema.html).


## Relevant Repository and Libraries
The following repositories are used for data collection.

### Geolocation Selector
The repository [`openlayer_selectlocation`](https://www.github.com/niebert/openlayer_selectlocation) are used to select a geolocation from an [OpenLayers](https://www.openlayers.org) map.

### Display Markers on the Map
The repository [`openlayer_display_markers`](https://www.github.com/niebert/openlayer_display_markers) to display all collected JSON records as markers with [OpenLayers](https://www.openlayers.org) map.

### JSON to Schema Generator

Used the following tool that creates a [JSON schema](http://json-schema.org/) for a provided JSON file. Used the given JSON file to create the JSON Schema with [JSON2schema.html](https://niebert.github.io/json-editor/plugins/json2schema.html).

## Acknowledgement
Special thanks to the following individual developers and teams of OpenSource JavaScript projects:
* [JSON-Editor](https://github.com/jdorn/json-editor) by Jeremy Dorn. The JSON Editor takes a JSON Schema and uses it to generate an HTML form. The JSON-Editor is partially used to edit JSON file of the Javascript Project in `JSCC` . The schemes of the JSON subtree are stored in the folder `/tpl` of the JavascriptClassCreator. The full potential of the JSON-Editor was not used in `JSCC` . This can be approved in the future.
The JSON-Editor of Jeremy Dorn has full support for JSON Schema version 3 and 4 and can integrate with several popular CSS frameworks (bootstrap, foundation, and jQueryUI). This would lead to major code reduction of `JSCC` . Refactoring of `JSCC` would make more use of the JSON-Editor features. Check out an interactive demo (demo.html): http://jeremydorn.com/json-editor/
* Developer [Mihai Bazon](http://lisperator.net/) create UglifyJS, a great tool to handle and parse Javascript Code and minify the Javascript code (see [Source Code of UglifyJS](https://github.com/mishoo/UglifyJS2)).
* The wrapper for UglifyJS is written [Dan Wolff](http://danwolff.se/). His UglifyJS-Online example is used to minify/compress the exported Javascript code of generated JS Classes (For Online Example of the [UglifyJS-Wrapper](https://skalman.github.io/UglifyJS-online/) see source code on https://github.com/Skalman/UglifyJS-online for the Online-Version of the Wrapper.
* Developers of ACE Code Editor https://ace.c9.io (Javascript Editing uses the Editor in iFrames)
* [FileSaver.js](https://github.com/eligrey/FileSaver.js) Developer Eli Grey provided the `FileSaver.js` that is used to store created `JSCC` files to the local filesystem. `JSCC` uses the same mechanism of browsers, that allows a `Save as...` in the context menu of a web pages or image. So not uncontrolled write access to your file system is implemented, because users have to select the locations in which the user whats to store the file (e.g. JSON, Javascript or HTML).
* [JointJS](https://github.com/clientIO/joint) JointJS is a JavaScript diagramming library. It can be used to create either static diagrams. JointJS is used in this project to create UML-diagrams, that are interactive diagramming in conjunction and application builder in Javascript.
* [Inheritage for JavaScript with protoypes](http://phrogz.net/js/classes/OOPinJS2.html) by Gavin Kistner
* [3 ways to define a JavaScript class](https://www.phpied.com/3-ways-to-define-a-javascript-class/) by Stoyan Stefanov
* [JQuery](https://jqueryui.com) is used for the theme and standard operations in the Document Object Model (DOM) of HTML-pages. The [JQuery-Themeroller](https://jqueryui.com/themeroller/) was used to create a JQuery theme for JSCC.
* [FontAwesome](http://fontawesome.io/icons/) by Dave Gandy used for the icons in HTML buttons
