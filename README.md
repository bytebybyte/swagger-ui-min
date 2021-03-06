# swagger-ui-min

## what?

This is a genuinely local-dependency free version of Swagger UI.

It's a single `index.html` with most dependencies loaded from [cdnjs.com](https://cdnjs.com).

You can simply serve up `index.html` as a static file then point your users at `<path/to/index.html>?url=<your/swagger.json>`.

## how?

* I forked swagger-ui and [made all changes here](https://github.com/csabapalfi/swagger-ui/blob/cdn/dist/index.html).
* This module grabs the new local-dependency free [`dist/index.html`](/dist/index.html)
* which is then [published to npm](https://www.npmjs.com/package/swagger-ui-min)

## why?

* this package is 4.4KB (swagger-ui is 5.7MB)
* single file, no need to serve all swagger-ui assets

## caveats

### no OAuth

This is the only major feature missing. The swagger-ui JS bundle might have it but I didn't have time to check so commented out the `initOAuth` call. See [index.html#L102](dist/index.html#L102)

### minor missing features

Some minor features are also missing in this version:

* no favicon for the page (couldn't care less)
* no print.css (seriously, who prints this?)
* no translation support
* syntax highlight only for JSON and XML

### embedded dependencies (not found on cdnjs):

I embedded the following scripts on the page (as they weren't on cdnjs):
* `object-assign-pollyfill.js`
* `jquery.slideto.min.js`
* `jquery.wiggle.min.js`
* the [compatibility patch from `backbone.min.js`](https://github.com/swagger-api/swagger-ui/blob/master/lib/backbone-min.js)
