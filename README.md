# iso-8859-13 [![Build status](https://travis-ci.org/mathiasbynens/iso-8859-13.svg?branch=master)](https://travis-ci.org/mathiasbynens/iso-8859-13) [![Code coverage status](https://coveralls.io/repos/mathiasbynens/iso-8859-13/badge.svg)](https://coveralls.io/r/mathiasbynens/iso-8859-13) [![Dependency status](https://gemnasium.com/mathiasbynens/iso-8859-13.svg)](https://gemnasium.com/mathiasbynens/iso-8859-13)

_iso-8859-13_ is a robust JavaScript implementation of [the iso-8859-13 character encoding as defined by the Encoding Standard](https://encoding.spec.whatwg.org/#iso-8859-13).

This encoding is known under the following names: iso-8859-13, iso8859-13, and iso885913.

## Installation

Via [npm](https://www.npmjs.com/):

```bash
npm install iso-8859-13
```

In a browser:

```html
<script src="iso-8859-13.js"></script>
```

In [Node.js](https://nodejs.org/), [io.js](https://iojs.org/), [Narwhal](http://narwhaljs.org/), and [RingoJS](http://ringojs.org/):

```js
var iso885913 = require('iso-8859-13');
```

In [Rhino](https://www.mozilla.org/rhino/):

```js
load('iso885913.js');
```

Using an AMD loader like [RequireJS](http://requirejs.org/):

```js
require(
  {
    'paths': {
      'iso-8859-13': 'path/to/iso-8859-13'
    }
  },
  ['iso-8859-13'],
  function(iso885913) {
    console.log(iso885913);
  }
);
```

## API

### `iso885913.version`

A string representing the semantic version number.

### `iso885913.labels`

An array of strings, each representing a [label](https://encoding.spec.whatwg.org/#label) for this encoding.

### `iso885913.encode(input, options)`

This function takes a plain text string (the `input` parameter) and encodes it according to iso-8859-13. The return value is a ‘byte string’, i.e. a string of which each item represents an octet as per iso-8859-13.

```js
const encodedData = iso885913.encode(text);
```

The optional `options` object and its `mode` property can be used to set the [error mode](https://encoding.spec.whatwg.org/#error-mode). For encoding, the error mode can be `'fatal'` (the default) or `'html'`.

```js
const encodedData = iso885913.encode(text, {
  'mode': 'html'
});
// If `text` contains a symbol that cannot be represented in iso-8859-13,
// instead of throwing an error, it will return an HTML entity for the symbol.
```

### `iso885913.decode(input, options)`

This function takes a byte string (the `input` parameter) and decodes it according to iso-8859-13.

```js
const text = iso885913.decode(encodedData);
```

The optional `options` object and its `mode` property can be used to set the [error mode](https://encoding.spec.whatwg.org/#error-mode). For decoding, the error mode can be `'replacement'` (the default) or `'fatal'`.

```js
const text = iso885913.decode(encodedData, {
  'mode': 'fatal'
});
// If `encodedData` contains an invalid byte for the iso-8859-13 encoding,
// instead of replacing it with U+FFFD in the output, an error is thrown.
```

For decoding a buffer (e.g. from `fs.readFile`) use `buffer.toString('binary')` to get the byte string which `decode` takes.

## Support

_iso-8859-13_ is designed to work in at least Node.js v0.10.0, io.js v1.0.0, Narwhal 0.3.2, RingoJS 0.8-0.11, PhantomJS 1.9.0, Rhino 1.7RC4, as well as old and modern versions of Chrome, Firefox, Safari, Opera, Edge, and Internet Explorer.

## Notes

[Similar modules for other single-byte legacy encodings are available.](https://www.npmjs.com/browse/keyword/legacy-encoding)

## Author

| [![twitter/mathias](https://gravatar.com/avatar/24e08a9ea84deb17ae121074d0f17125?s=70)](https://twitter.com/mathias "Follow @mathias on Twitter") |
|---|
| [Mathias Bynens](https://mathiasbynens.be/) |

## License

_iso-8859-13_ is available under the [MIT](https://mths.be/mit) license.
