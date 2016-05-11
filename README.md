# base-files-process [![NPM version](https://img.shields.io/npm/v/base-files-process.svg?style=flat)](https://www.npmjs.com/package/base-files-process) [![NPM downloads](https://img.shields.io/npm/dm/base-files-process.svg?style=flat)](https://npmjs.org/package/base-files-process) [![Build Status](https://img.shields.io/travis/node-base/base-files-process.svg?style=flat)](https://travis-ci.org/node-base/base-files-process)

Plugin for processing files from a declarative configuration.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install base-files-process --save
```

## Usage

```js
var files = require('base-files-process');
```

## Example

```js
var expand = require('expand-files');
var Base = require('base');
var pipeline = require('base-pipeline');
var files = require('base-files-process');
var vfs = require('base-fs');
var app = new Base();

app.use(pipeline());
app.use(files());
app.use(vfs());

// register pipeline plugins using the `.plugin` method
app.plugin('foo', function(options) {
  return through.obj(function(file, enc, next) {
    // do plugin stuff 
    next(null, file);
  });
});

// use `expand-files` to expand a declarative configuration object
config = expand({
  cwd: fixtures,
  src: '*.txt',
  dest: actual
});

// pass the config object to `.process()`
app.process(config)
  .on('end', function() {
    console.log('done!');
  });
```

## Related projects

You might also be interested in these projects:

* [base-fs](https://www.npmjs.com/package/base-fs): base-methods plugin that adds vinyl-fs methods to your 'base' application for working with the file… [more](https://www.npmjs.com/package/base-fs) | [homepage](https://github.com/node-base/base-fs)
* [base-pipeline](https://www.npmjs.com/package/base-pipeline): base-methods plugin that adds pipeline and plugin methods for dynamically composing streaming plugin pipelines. | [homepage](https://github.com/node-base/base-pipeline)
* [base-task](https://www.npmjs.com/package/base-task): base plugin that provides a very thin wrapper around [https://github.com/doowb/composer](https://github.com/doowb/composer) for adding task methods to… [more](https://www.npmjs.com/package/base-task) | [homepage](https://github.com/node-base/base-task)
* [base](https://www.npmjs.com/package/base): base is the foundation for creating modular, unit testable and highly pluggable node.js applications, starting… [more](https://www.npmjs.com/package/base) | [homepage](https://github.com/node-base/base)

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/node-base/base-files-process/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install verb && npm run docs
```

Or, if [verb](https://github.com/verbose/verb) is installed globally:

```sh
$ verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/node-base/base-files-process/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on May 11, 2016._