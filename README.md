# body-parser-multidict

[![Build Status][travis-image]][travis-url]

Fork of [body-parser][] with [Werkzeug's MultiDict support][multidict] for urlencoded forms

We built `querystring-multidict` for consistent typing when reading query strings (e.g. `.get()` always returns a single string value whereas `querystring`/`qs` can return an array/object depending on user input). Additionally, we added `.fetch()` to make throwing form validation errors easier.

[travis-image]: https://img.shields.io/travis/twolfson/body-parser-multidict/master.svg
[travis-url]: https://travis-ci.org/twolfson/body-parser-multidict
[body-parser]: https://github.com/expressjs/body-parser
[multidict]: https://github.com/twolfson/querystring-multidict/tree/1.0.0#multidict

## Getting Started
This module can be installed via: `npm install body-parser-multidict`

Its usage is the same as `body-parser`:

```js
// Load in our dependencies
var express = require('express');
var bodyParserMultiDict = require('body-parser-multidict');

// Create a new app using our urlencoded parser
var app = express();
app.use(bodyParser.urlencoded());

// Handle requests
app.use(function (req, res) {
  // Example request: `POST foo=bar&foo=baz`
  // First received value under key
  req.body.get('foo'); // 'bar'
  // Array of values received under key
  req.body.getArray('foo');// ['bar', 'baz']
});
```

## Documentation
Documentation is the same as [body-parser][] except `req.body` is a `MultiDict`. See `querystring-multidict` for `MultiDict` documentation:

https://github.com/twolfson/querystring-multidict/tree/1.1.0#multidict

## License

[MIT](LICENSE)

