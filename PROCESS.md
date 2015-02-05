### 3. API edition

Let's start at the end.

Eventually, there will be a Tiddlywiki **API** edition that contains appropriately titled **documentation tiddlers** that reference the code-elements they relate to. A conditional ViewTemplate will render, e.g. slide open, the corresponding shadow tiddler. The parser will extract all required information to know for each documentation tiddler precisely what object in the browser memory it relates to, so we can even render that function in-place. Later we may  also implement a side-by-side view of code and comments, since we know during parsing what line of code a given documentation comment block refers to.

### 2. build-doc

There will be a dedicated build process, parsing all **.js** tiddlers of master,  translating the documentation comment blocks in each module into **documentation tiddlers** and outputting them into a dedicated folder in the API edition. There will be folders in the API edition that remain untouched by the build-doc process as there are components in the API wiki not generated by the build process, e.g. macros, styles, conditional templates, menus, etc..

### 1. code comments

To actually comment the javascript code, we use a simple **.tid** file based [format](FORMAT.md) to document files (aka modules), functions, properties. The format is such that we could actually save each comment block as a *.tid* file and import it into TiddlyWiki. However, some fields of that *.tid* file are actually not explicitly documented but rather implicit, auto-generated, most prominently the tiddler title itself.