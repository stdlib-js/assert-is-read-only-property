<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# isReadOnlyProperty

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] [![dependencies][dependencies-image]][dependencies-url]

> Test if an object's own property is [read-only][@stdlib/utils/define-read-only-property].

<section class="installation">

## Installation

```bash
npm install @stdlib/assert-is-read-only-property
```

</section>

<section class="usage">

## Usage

```javascript
var isReadOnlyProperty = require( '@stdlib/assert-is-read-only-property' );
```

#### isReadOnlyProperty( value, property )

Returns a `boolean` indicating if a `value` has a [read-only][@stdlib/utils/define-read-only-property] `property`.

<!-- eslint-disable no-restricted-syntax -->

```javascript
var defineProperty = require( '@stdlib/utils-define-property' );

var obj = {
    'foo': 'bar'
};

defineProperty( obj, 'beep', {
    'configurable': false,
    'enumerable': false,
    'writable': false,
    'value': 'boop'
});

defineProperty( obj, 'accessor', {
    'configurable': false,
    'enumerable': true,
    'get': function getter() {
        return obj.foo;
    }
});

var bool = isReadOnlyProperty( obj, 'foo' );
// returns false

bool = isReadOnlyProperty( obj, 'beep' );
// returns true

bool = isReadOnlyProperty( obj, 'accessor' );
// returns true
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Value arguments other than `null` or `undefined` are coerced to `objects`.

    ```javascript
    var bool = isReadOnlyProperty( 'beep', 'length' );
    // returns true
    ```

-   Property arguments are coerced to `strings`.

    ```javascript
    var defineProperty = require( '@stdlib/utils-define-property' );

    var obj = {};

    defineProperty( obj, 'null', {
        'configurable': false,
        'enumerable': true,
        'writable': false,
        'value': true
    });

    var bool = isReadOnlyProperty( obj, null );
    // returns true
    ```

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint-disable object-curly-newline -->

<!-- eslint no-undef: "error" -->

```javascript
var isReadOnlyProperty = require( '@stdlib/assert-is-read-only-property' );

var bool = isReadOnlyProperty( 'a', 'length' );
// returns true

bool = isReadOnlyProperty( { 'a': 'b' }, 'a' );
// returns false

bool = isReadOnlyProperty( [ 'a' ], 0 );
// returns false

bool = isReadOnlyProperty( { 'null': false }, null );
// returns false

bool = isReadOnlyProperty( { '[object Object]': false }, {} );
// returns false

bool = isReadOnlyProperty( {}, 'toString' );
// returns false

bool = isReadOnlyProperty( {}, 'hasOwnProperty' );
// returns false

bool = isReadOnlyProperty( null, 'a' );
// returns false

bool = isReadOnlyProperty( void 0, 'a' );
// returns false
```

</section>

<!-- /.examples -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/assert-is-read-only-property.svg
[npm-url]: https://npmjs.org/package/@stdlib/assert-is-read-only-property

[test-image]: https://github.com/stdlib-js/assert-is-read-only-property/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/assert-is-read-only-property/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/assert-is-read-only-property/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/assert-is-read-only-property?branch=main

[dependencies-image]: https://img.shields.io/david/stdlib-js/assert-is-read-only-property.svg
[dependencies-url]: https://david-dm.org/stdlib-js/assert-is-read-only-property/main

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://gitter.im/stdlib-js/stdlib/

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/assert-is-read-only-property/main/LICENSE

[@stdlib/utils/define-read-only-property]: https://github.com/stdlib-js/utils-define-read-only-property

</section>

<!-- /.links -->
