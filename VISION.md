### 1. Eat Your Own Dogfood

* the TiddlyWiki API documentation is a TiddlyWiki and built by one
	* API Documentation comment blocks do not end up in the TiddlyWiki build
* most of the API documentation logic is build within the API TiddlyWiki
	* rather than implemented in a comment parser
* no 3rd party rendering libraries / external dependencies
	* except for plugins in that API TiddlyWiki, e.g. higlight.js or CodeMirror 

### 2. KISS

* keep it simple and smart
* use **.tid** format for documentation blocks => TiddlyWiki style "WYSYWIG"
* jsdoc parser to cater for other projects? => later!
* output formats other than TiddlyWiki? => later!

### 3. Contributing

* make it easy for people to contribute code documentation
* simple, straight forward guidelines
* GitHub pull requests
