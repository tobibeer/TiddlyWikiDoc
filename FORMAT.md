### Build vs. Documentation

* currently, the head of each js file contains a build-comment-block
    * will be reduced to required fields
    * all prose will go into...

### Documentation Blocks

Documentation blocks are comment blocks that start with two asterisks, e.g.

```
/**
_argument: value
__docfield: value
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
* all documentation specific fields are prefixed with **_underscore**
    * especially `_return` and each individual `_argument`
    * so as to avoid clashes with standard tiddler fields
    * specific documentation fields are given two `__underscores` so as to avoid clashes with arguments
* all regular fields are specified as-is, e.g. tags
* for each documented module or function a `//single comment line` shall remain immediately above it
    * to summarize the module or function, saved in a `__summary` field
    * thus, each function at least has a summary giving an indication as to what it does
        * assuming simple comments will remain in the final TiddlyWiki build — to be discussed

### Content

The content type for each block should be globally configurable for the **build-doc** parser and default to `text/vnd.tiddlywiki`, alternatively `text/x-markdown`. This can be overriden for individual documentation blocks simply by setting the type field accordingly...

```
/**
type: text/x-markdown

# Documentation
Using markdown...
*/
```

### Module Documentation

Each module (/file) will have a documentation block following the build block, e.g.

```
/*\
title: $:/core/modules/filters/listed.js
type: application/javascript
module-type: filteroperator
\*/
/**
__namespace: $tw.Wiki.prototype.filterOperators.listed
*/
//Filter operator returning all tiddlers that have the selected tiddlers in a list
(function(){
```

* documents the module as a whole in the sense of an introduction
* for each module a `__namespace` is defined refering to the actual object to which its functions by default apply
    * in the case of a filter it's pretty much the function itself rather than a module, see [examples](EXAMPLES.md)

### Function Documentation

```
/**
_return: {String} the text contained in the TextReference
_textRef: {String} a TextReference
_defaultText: {String} the default text returned when undefined
_currTiddlerTitle: {String} the CurrentTiddler, e.g. for `{{!!field}}`
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

* **_return** — the return value
   * preferably listed first for readability
* **_argument** — each argument is prefixed with `_`
   * should follow **_return** for readability
* **title** — is calculated for each **documentation tiddler** as a concatenation of...
    * the `__namespace` defined for the module
        * can be overwritten by declaring a `_namespace` at the function documentation
    * `.` — a dot
    * the name of the function as extracted by the parser
* **__arguments** — the actual arguments are parsed from the function head, removing commas
   * perhaps stored with underscores to simplify handling in TiddlyWiki
* **__function** — the function title by itself
* **__namespace** — the applied namespace by itself
* **__summary** — the comment line above the function head
* **__module** — the module title
* **__folder** — the folder in which the file resides
* **__file** — the filepath of the module holding the code
* **__line** — the line of code where the function is defined

### Nice To Have Fields
* a `__released` — the release number when a function or module was first introduced
* a `__modified` — all release numbers when the function was touched, listed descending
