ic-styled
=========

Automatically style components with css templates.

Installation
------------

`bower install ic-styled`

`npm install ic-styled`

... or download `main.js` and include it into your app however you want.

Module Support
--------------

- AMD

  `define(['ic-styled'], function(Styled) {});`

- CJS

  `var Styled = require('ic-styled')`

- Globals

  `var Styled = ic.Styled;`

  All instructure canvas stuff lives on the `ic` global.

Usage
-----

Given a component named `x-foo`, create an additional component template
at `components/x-foo-css`, treat it like a css file, then mixin `Styled`
to `x-foo` and `x-foo-css` will be imported into your app automatically
on the first instance of `x-foo`.

Sounds tricky but its not; here's a sample app:

```html
<script type="text/x-handlebars">
  <h1>Application Template using x-foo</h1>
  {{x-foo}}
</script>

<script type="text/x-handlebars" id="components/x-foo">
  I am x-foo, the main component.
</script>

<script type="text/x-handlebars" id="components/x-foo-css">
  /* I am x-foo-css, the styles that go with x-foo */
  x-foo { color: red; font-weight: bold; }
</script>

<script>
  var App = Ember.Application.create();
  var Styled = ic.Styled;
  App.XFooComponent = Ember.Component.extend(Styled, {
    tagName: 'x-foo'
  });
</script>
```

At the first render of `{{x-foo}}` the `{{x-foo-css}}` template is
imported into the app to style `x-foo` elements.

Overriding Component Styles
---------------------------

`Styled` injects the css template to the top of the `<head>` element so
its the first-ish css to be applied. This means that you can override
the CSS of styled components the same as any native element since your
app's CSS will be applied after.

Contributing
------------

```sh
bower install
npm install
npm test
```

License and Copyright
---------------------

MIT Style license

(c) 2013 Instructure, Inc.

