## filters

(Most) Filters only contain a single function, the filter itself. Hence, there will only be a single tiddler for each filter, e.g. **/core/modules/filters/backlinks** which documents the filter on a file basis.

The parameters for the filter function need not be explicitly documented at every single filter as they are common throughout all filters, documented in a dedicated block at **filters.js** itself.

The reference to **filters.js** will be established by a module in the API wiki, e.g. a conditional ViewTemplate that knows we're looking at a `moduletype=filteroperator` and hence render a backlink to **filters.js**.
