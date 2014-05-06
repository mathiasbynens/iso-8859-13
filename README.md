# iso-8859-13 [![Build status](https://travis-ci.org/mathiasbynens/iso-8859-13.svg?branch=master)](https://travis-ci.org/mathiasbynens/iso-8859-13) [![Dependency status](https://gemnasium.com/mathiasbynens/iso-8859-13.svg)](https://gemnasium.com/mathiasbynens/iso-8859-13)

_iso-8859-13_ is robust JavaScript implementation of [the iso-8859-13 character encoding as defined by the Encoding Standard](http://encoding.spec.whatwg.org/#iso-8859-13).

This encoding is known under the following names: iso-8859-13, iso8859-13, iso885913, and iso885913.

## Installation

Via [npm](http://npmjs.org/):

```bash
npm install iso-8859-13
```

Via [Bower](http://bower.io/):

```bash
bower install iso-8859-13
```

Via [Component](https://github.com/component/component):

```bash
component install mathiasbynens/iso-8859-13
```

In a browser:

```html
<script src="iso-8859-13.js"></script>
```

In [Narwhal](http://narwhaljs.org/), [Node.js](http://nodejs.org/), and [RingoJS](http://ringojs.org/):

```js
var iso885913 = require('iso-8859-13');
```

In [Rhino](http://www.mozilla.org/rhino/):

```js
load('iso885913.js');
```

Using an AMD loader like [RequireJS](http://requirejs.org/):

```js
require(
  {
    'paths': {
      'iso885913': 'path/to/iso885913'
    }
  },
  ['iso885913'],
  function(iso885913) {
    console.log(iso885913);
  }
);
```

## API

### `iso885913.version`

A string representing the semantic version number.

### `iso885913.encode(input, options)`

This function takes a plain text string (the `input` parameter) and encodes it according to iso-8859-13. The return value is a ‘byte string’, i.e. a string of which each item represents an octet as per iso-8859-13.

```js
var encodedData = iso885913.encode(text);
```

The optional `options` object and its `mode` property can be used to set the [error mode](http://encoding.spec.whatwg.org/#error-mode). For encoding, the error mode can be `'fatal'` (the default) or `'html'`.

```js
var encodedData = iso885913.encode(text, {
  'mode': 'html'
});
// If `text` contains a symbol that cannot be represented in iso-8859-13,
// instead of throwing an error, it will return an HTML entity for the symbol.
```

### `iso885913.decode(input, options)`

This function takes a byte string (the `input` parameter) and decodes it according to iso-8859-13.

```js
var text = iso885913.decode(encodedData);
```

The optional `options` object and its `mode` property can be used to set the [error mode](http://encoding.spec.whatwg.org/#error-mode). For decoding, the error mode can be `'replacement'` (the default) or `'fatal'`.

```js
var text = iso885913.decode(encodedData, {
  'mode': 'fatal'
});
// If `encodedData` contains an invalid byte for the iso-8859-13 encoding,
// instead of replacing it with U+FFFD in the output, an error is thrown.
```

## Support

_iso-8859-13_ is designed to work in at least Node.js v0.10.0, Narwhal 0.3.2, RingoJS 0.8-0.9, PhantomJS 1.9.0, Rhino 1.7RC4, as well as old and modern versions of Chrome, Firefox, Safari, Opera, and Internet Explorer.

## Unit tests & code coverage

After cloning this repository, run `npm install` to install the dependencies needed for development and testing. You may want to install Istanbul _globally_ using `npm install istanbul -g`.

Once that’s done, you can run the unit tests in Node using `npm test` or `node tests/tests.js`. To run the tests in Rhino, Ringo, Narwhal, and web browsers as well, use `grunt test`.

To generate the code coverage report, use `grunt cover`.

## Author

| [![twitter/mathias](https://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](https://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](http://mathiasbynens.be/) |

## License

_iso-8859-13_ is available under the [MIT](http://mths.be/mit) license.