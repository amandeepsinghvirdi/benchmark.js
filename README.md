# Benchmark.js v2.0.0-pre

A [robust](http://calendar.perfplanet.com/2010/bulletproof-javascript-benchmarks/ "Bulletproof JavaScript benchmarks") benchmarking library that supports high-resolution timers & returns statistically significant results. As seen on [jsPerf](http://jsperf.com/).

## Documentation

* [API Documentation](http://benchmarkjs.com/docs)
* Check out our [unit tests](http://benchmarkjs.com/tests) & [roadmap](https://github.com/bestiejs/benchmark.js/wiki/Roadmap)

## Download

 * [Development source](https://raw.github.com/bestiejs/benchmark.js/v1.0.0/benchmark.js)

## Installation

Benchmark.js’ only hard dependency is [Lo-Dash](https://lodash.com/).
Include [platform.js](http://mths.be/platform) to populate [Benchmark.platform](http://benchmarkjs.com/docs#platform).

In a browser:

```html
<script src="lodash.js"></script>
<script src="platform.js"></script>
<script src="benchmark.js"></script>
```

Optionally, expose Java’s nanosecond timer by adding the `nano` applet to the `<body>`:

```html
<applet code="nano" archive="nano.jar"></applet>
```

Or enable Chrome’s microsecond timer by using the [command line switch](http://peter.sh/experiments/chromium-command-line-switches/#enable-benchmarking):

```
  --enable-benchmarking
```

In an AMD loader:

```js
require({
  'paths': {
    'benchmark': 'path/to/benchmark',
    'lodash': 'path/to/lodash',
    'platform': 'path/to/platform'
  }
},
['benchmark'], function(Benchmark) {/*…*/});
```

Using npm:

```bash
$ npm i --save benchmark
```

In Node.js:

```js
var Benchmark = require('benchmark');
```

Optionally, use the [microtime module](https://github.com/wadey/node-microtime) by Wade Simmons:

```bash
npm install microtime
```

Usage example:

```js
var suite = new Benchmark.Suite;

// add tests
suite.add('RegExp#test', function() {
  /o/.test('Hello World!');
})
.add('String#indexOf', function() {
  'Hello World!'.indexOf('o') > -1;
})
// add listeners
.on('cycle', function(event) {
  console.log(String(event.target));
})
.on('complete', function() {
  console.log('Fastest is ' + this.filter('fastest').pluck('name'));
})
// run async
.run({ 'async': true });

// logs:
// => RegExp#test x 4,161,532 +-0.99% (59 cycles)
// => String#indexOf x 6,139,623 +-1.00% (131 cycles)
// => Fastest is String#indexOf
```

## Support

Tested in Chrome 38-39, Firefox 34-35, IE 6-11, Opera 25-26, Safari 5-8, Node.js 0.8.28 & 0.10.35, PhantomJS 1.9.8, RingoJS 0.11, & Rhino 1.7RC5.

## BestieJS

Benchmark.js is part of the BestieJS *“Best in Class”* module collection. This means we promote solid browser/environment support, ES5+ precedents, unit testing, & plenty of documentation.
