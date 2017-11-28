*Let's talk about Javascript!*

Toolchain
===

* jQuery (Javascript: The Missing Parts)
* Backbone (MVC framework)
* Underscore (extensions library)
* Marionette (backbone plugin)
* Handlebars (templating library)
* jasmine (testing framework)
* jshint (linting tool via Overcommit)

Architecture
===

* Rails server data
  We get data from Rails in two ways general ways, and sometimes refresh content through a third
    * Embedded data:
      Sometimes the JS needs to operate on data immediately - waiting for the page to load and then using AJAX to populate the page data would be too slow and a bad user experience.
      Instead, we make content-free div tags with an ID related to the kind of data being rendered and `data-` attributes wrapping the serialized data from the server.
      This can be seen for the Addons backer survey page in `views/backers/_cart.html.erb`:
        
        `<%= content_tag("div",'', id: "existing_line_items", data: {items: @line_items }) %>`

      Data divs such as this should always nest the Rails data (e.g. `@line_items`, which is an array of line item records wrapped in serializers) in a top-level key, because jQuery reading the keys out of data transforms key names into camel-cased strings for the top level, but does not recurse into the encoded data
      To read this data into JS, we use the utility function `BackerKit.utils.getData(<selector>)` and then read the property `.<topLevelKeyName>` out of that return object.

    * AJAX data: 
      Sometimes we read JSON from various API endpoints after the page has already been created.
      As much as possible we should try and use RESTful APIs and Backbone models/collections to manage this data,
      but sometimes the endpoint is unable to respond with a good result immediately,
      and instead we create a background job in Rails and return that job's ID.
      Polling a Job endpoint with that ID will return the current job status and eventually response data that the page may need to continue its workflow.

    * Asynchronous server-rendered HTML:
      This technique is mostly used for modal content - this kind of request receives an HTML response page with one or many top-level tags.
      Each of those tags should have an ID that may be used to replace any existing tags on the page with matching IDs. 
      This is a pattern we should probably avoid as much as possible because replacement DOM may not properly interact with existing event bindings and view structures.

* Globals
  We have a couple existing globals available on most pages within the site - `currentBacker` and `currentAdmin` most notably, but also `window.BackerKit` itself.
  We prefer to manage globals through the `BackerKit.Globals` namespace, because various libraries and third party scripts (google analytics, etc) pollute the `window` namespace,
  and it is easier to manage that `Globals` object in test than it is to manage all variables that may have been added to the `window` top level namespace.

* routers
  Backbone provides Routers as objects that can detect the current 
  We instantiate all routes
* views
  * binding to existing dom vs rendering own dom
  * events
  * render pipeline
  * pages
  * modals
  * components
* models
* collections

Lifecycle
===

How does our JS system start on a Rails-served page?
---
How do we test JS?
---
* jasmine unit tests
* specdom
* jasmine ajax
* util overrides
* debugger
* how do we test JS behavior in feature specs?

History
===
lol
