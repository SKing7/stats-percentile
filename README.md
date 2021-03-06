# Percentile [![Build Status](https://travis-ci.org/msn0/stats-percentile.svg?branch=master)](http://travis-ci.org/msn0/stats-percentile)

> Calculate n-th percentile of data using [Nearest Rank Method](http://en.wikipedia.org/wiki/Percentile#The_Nearest_Rank_method).

## Installation

```sh
npm install stats-percentile
```

## Usage

```js
var percentile = require('stats-percentile');

var data = [3, 6, 7, 8, 8, 10, 13, 15, 16, 20];

percentile.calc(data, 75); // → 15
```

### API

#### calc(data, n)

##### data

Type: `array`

The data to be analysed; an array of numbers.

##### n

Type: `number`

n-th percentile to calculate; a number between 0 and 100. 

## Alogrithm

Internally, `calc` applies a O(n) algorithm for k'th largest element problem, which get a better performance than ordinary sort method. The following benchmark result can tell more:

```
percentile#findK x 116,079 ops/sec ±0.54% (97 runs sampled)
percentile#sort x 16,077 ops/sec ±0.90% (98 runs sampled)
Fastest is percentile#findK
```
`percentile 不需要进行完全排序，只需要逐步定位到百分位的区域内，所以findK的这种基于quickSort的算法的复杂度降到了o(n)`

## License
MIT &copy; [Michał Jezierski](https://pl.linkedin.com/in/jezierskimichal)
