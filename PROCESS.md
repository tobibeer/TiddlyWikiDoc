From code-comments to the API documentation. Let's start at the end.

### 3. API edition

* eventually, there will be a Tiddlywiki **API** edition
    * containing appropriately titled **documentation tiddlers** referencing the code-elements they relate to
* a conditional view-template will render, e.g. slide open, the corresponding code or shadow tiddler
* the **build-doc** parser extracts all required information
   * so that we know for each documentation tiddler precisely what object in the browser memory it relates to
   * allowing us to  render that function in-place
* later we may  also implement a side-by-side view of code and comments
    * as we know during parsing what line of code a given documentation comment block refers to

### 2. build-doc

A dedicated build process will..
* parse all **.js** tiddlers of master
* translate the documentation comment blocks in each module into **documentation tiddlers**
* output **documentation tiddlers** into a dedicated folder in the API edition
* leave other folders in the API edition untouched
    * e.g. macros, styles, conditional templates, menus, etc.

### 1. code comments

* to actually comment the javascript code, we use a simple **.tid** file based [format](FORMAT.md)
    * documenting files (aka modules), functions, properties
* the format is such that we could actually save each comment block as a *.tid* file and import it into TiddlyWiki
    * however, some fields of that *.tid* file are not explicitly documented but rather implicit, auto-generated
        * most prominently the tiddler title itself
