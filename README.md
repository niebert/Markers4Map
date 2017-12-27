# Markers4Map
OpenLayers create a JSON Database of Markers for the Map


## Online Demo

https://niebert.github.io/Markers4Map

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
