### Build vs. Documentation

* currently, the head of each js file contains a build-comment-block
    * will be reduced to required fields
    * all prose will go into...

### Documentation Blocks

Documentation blocks are comment blocks that start with two asterisks, e.g.

```
/**
_field: value
tags: foo bar

text
*/
//summary
(function(){
```

* the contents in the documentation block follow **tid** file formatting rules
    * e.g. starting out with field declarations
    * then a newline
    * followed by the documentation content
* all documentation specific fields are  prefixed with **_underscore**
    * so as to avoid clashes with standard tiddler fields
* all regular fields are specified as-is, e.g. tags
* for each documented module or function a `//single comment line` shall remain immediately above it
    * to summarize the module or function, saved in a `_summary` field
    * thus, each function at least has a summary giving an indication as to what it does
        * assuming simple comments will remain in the final TiddlyWiki build — to be discussed

### Module Documentation

Each module (/file) will have a documentation block following the build block, e.g.

```
/*\
title: $:/core/modules/filters/listed.js
type: application/javascript
module-type: filteroperator
\*/
/**
_namespace: $tw.Wiki.prototype.filterOperators.listed
*/
//Filter operator returning all tiddlers that have the selected tiddlers in a list
(function(){
```

* documents the module as a whole in the sense of an introduction
* each module block defines a namespace refering to the object to which its functions by default apply
    * in the case of a filter it's pretty much the function itself rather than a module, see [examples](EXAMPLES.md)

### Function Documentation

```
/**
_return: {string} the text for the text reference
_textRef: {string} a TextReference
_defaultText: {string} the default text returned when undefined
_currTiddlerTitle: {string} the current tiddler's title, e.g. for `{{!!field}}`
tags: TextReferences

Text references can have any of these forms:

* `<tiddlertitle>`
* <tiddlertitle>!!<fieldname>`
* !!<fieldname> — a field of the CurrentTiddler`
* <tiddlertitle>##<index>` — for DataTiddlers
*/
//get the value of a text reference
exports.getTextReference = function(textRef,defaultText,currTiddlerTitle) {
```

* the return value is declared using `_return` and preferably listed first
* arguments are prefixed with `_` and should follow the `_return` value
* the calculated **title** of the **documentation tiddler** is a concatenation of...
    * the `_namespace` defined for the module
        * can be overwritten by declaring a `_namespace` at the function documentation
    * `.` — a dot
    * the name of the function as extracted by the parser
* the actual arguments are parsed from the function head, removing commas and stored in the `_arguments` field

### Optional Fields
* a `_released` field could specify the release number when a function or module was first introduced
* a `_modified` field could list all release numbers when a function was touched
