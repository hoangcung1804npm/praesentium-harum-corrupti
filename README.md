# @hoangcung1804npm/praesentium-harum-corrupti <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ESnext spec-compliant `Map.groupBy` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://tc39.github.io/proposal-array-grouping/).

## Getting started

```sh
npm install --save @hoangcung1804npm/praesentium-harum-corrupti
```

## Usage/Examples

```js
var groupBy = require('@hoangcung1804npm/praesentium-harum-corrupti');
var assert = require('assert');

var arr = [0, 1, 2, 3, 4, 5];
var parity = function (x) { return x % 2 === 0 ? 'even' : 'odd'; };

var results = groupBy(arr, function (x, i) {
    assert.equal(x, arr[i]);
    return parity(x);
});

assert.deepEqual(results, new Map([
    ['even', [0, 2, 4]],
    ['odd', [1, 3, 5]],
]));
```

```js
var groupBy = require('@hoangcung1804npm/praesentium-harum-corrupti');
var assert = require('assert');
/* when Map.groupBy is not present */
delete Map.groupBy;
var shimmed = groupBy.shim();

assert.equal(shimmed, groupBy.getPolyfill());
assert.deepEqual(Map.groupBy(arr, parity), groupBy(arr, parity));
```

```js
var groupBy = require('@hoangcung1804npm/praesentium-harum-corrupti');
var assert = require('assert');
/* when Array#group is present */
var shimmed = groupBy.shim();

assert.equal(shimmed, Map.groupBy);
assert.deepEqual(Map.groupBy(arr, parity), groupBy(arr, parity));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hoangcung1804npm/praesentium-harum-corrupti
[npm-version-svg]: https://versionbadg.es/hoangcung1804npm/praesentium-harum-corrupti.svg
[deps-svg]: https://david-dm.org/hoangcung1804npm/praesentium-harum-corrupti.svg
[deps-url]: https://david-dm.org/hoangcung1804npm/praesentium-harum-corrupti
[dev-deps-svg]: https://david-dm.org/hoangcung1804npm/praesentium-harum-corrupti/dev-status.svg
[dev-deps-url]: https://david-dm.org/hoangcung1804npm/praesentium-harum-corrupti#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hoangcung1804npm/praesentium-harum-corrupti.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hoangcung1804npm/praesentium-harum-corrupti.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hoangcung1804npm/praesentium-harum-corrupti.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hoangcung1804npm/praesentium-harum-corrupti
[codecov-image]: https://codecov.io/gh/hoangcung1804npm/praesentium-harum-corrupti/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/hoangcung1804npm/praesentium-harum-corrupti/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/hoangcung1804npm/praesentium-harum-corrupti
[actions-url]: https://github.com/hoangcung1804npm/praesentium-harum-corrupti/actions
