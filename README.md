Compute.io
==========
[![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coverage][coveralls-image]][coveralls-url] [![Dependencies][dependencies-image]][dependencies-url]

> Computation library.


## Table of Contents

1. 	[Installation](#installation)
1. 	[Usage](#usage)
	- 	[Utilities](#utilities)
		* 	[roundn( x, n )](#roundn)
		*	[polyval( coef, x )](#polyval)
		*	[reverse( arr )](#reverse)
		*	[shuffle( arr )](#shuffle)
		*	[circshift( x, k )](#circshift)
		*	[diff( arr )](#diff)
		*	[find( arr, opts, clbk )](#find)
		*	[deg2rad( x )](#deg2rad)
		*	[rad2deg( x )](#rad2deg)
		*	[issorted( arr, clbk )](#issorted)
		*	[isnan( arr )](#isnan)
	-	[Special Functions](#special-functions)
		*	[abs( arr )](#abs)
		*	[sqrt( arr )](#sqrt)
		*	[signum( x )](#signum)
		*	[erf( x )](#erf)
		*	[erfc( x )](#erfc)
		*	[erfinv( x )](#erfinv)
		*	[erfcinv( x )](#erfcinv)
	- 	[Arithmetic](#arithmetic)
		*	[add( arr, x )](#add)
		*	[subtract( arr, x )](#subtract)
		*	[multiply( arr, x )](#multiply)
		*	[divide( arr, x )](#divide)
	- 	[Sets](#sets)
		*	[unique( arr, sorted )](#unique)
	-	[Linear Algebra](#linear-algebra)
		* 	[l1norm( arr )](#l1norm)
		* 	[l2norm( arr )](#l2norm)
		* 	[linfnorm( arr )](#linfnorm)
		* 	[lpnorm( arr )](#lpnorm)
		*	[dot( x, y )](#dot)
		*	[cross( x, y )](#cross)
	- 	[Statistics](#statistics)
		*	[min( arr )](#min)
		*	[incrmin()](#incrmin)
		*	[mmin( arr, window )](#mmin)
		*	[cmin( arr )](#cmin)
		*	[max( arr )](#max)
		*	[incrmax()](#incrmax)
		*	[mmax( arr, window )](#mmax)
		*	[cmax( arr )](#cmax)
		*	[range( arr )](#range)
		*	[sum( arr )](#sum)
		*	[nansum( arr )](#nansum)
		*	[incrsum()](#incrsum)
		*	[msum( arr, window )](#msum)
		*	[csum( arr )](#csum)
		*	[mean( arr )](#mean)
		*	[nanmean( arr )](#nanmean)
		*	[incrmean()](#incrmean)
		*	[mmean( arr, window )](#mmean)
		*	[wmean( arr, weights )](#wmean)
		*	[gmean( arr )](#gmean)
		*	[nangmean( arr )](#nangmean)
		*	[hmean( arr )](#hmean)
		*	[nanhmean( arr )](#nanhmean)
		*	[qmean( arr )](#qmean)
		*	[nanqmean( arr )](#nanqmean)
		*	[variance( arr )](#variance)
		*	[nanvariance( arr )](#nanvariance)
		*	[incrvariance()](#incrvariance)
		*	[stdev( arr )](#stdev)
		*	[nanstdev( arr )](#nanstdev)
		*	[incrstdev()](#incrstdev)
		*	[mode( arr )](#mode)
		*	[median( arr, sorted )](#median)
		*	[quantile( arr, p, opts )](#quantile)
		*	[quantiles( arr, num, opts )](#quantiles)
		*	[iqr( arr, opts )](#iqr)
		*	[idr( arr, opts )](#idr)
		*	[midrange( arr, sorted )](#midrange)
		*	[midhinge( arr, opts )](#midhinge)
		*	[midsummary( arr, n, opts )](#midsummary)
		*	[midmean( arr, sorted )](#midmean)
		*	[trimean( arr, opts )](#trimean)
		*	[skewness( arr )](#skewness)
		*	[kurtosis( arr )](#kurtosis)
	-	[Geometry](#geometry)
		*	[hypot( a, b )](#hypot)
	- 	[Information Theory](#information-theory)
		*	[hamdist( a, b )](#hamdist)
1. 	[Fluent Interface](#fluent-interface)
1. 	[Tests](#tests)
	- 	[Unit](#unit)
	-	[Coverage](#test-coverage)
1. 	[License](#license)


## Installation

``` bash
$ npm install compute.io
```

## Usage

To use compute,

``` javascript
var compute = require( 'compute.io' );
```

The compute module is comprised of several smaller modules. If you want to roll your own compute, follow the links and import the individual modules.

The compute module has the following methods...


### Utilities

<a name="roundn"></a>
#### [compute.roundn( x, n )](https://github.com/compute-io/roundn)

Rounds values to the nearest multiple of `10^n`. `x` may be either a single numeric value or an array of values. `n` must be an `integer`.

``` javascript
compute.roundn( Math.PI, -2 );
// returns 3.14

var x = compute.roundn( 111, 2 );
// returns 100

var data = [ 2.342, 4.943, 2.234, 7.992, 3.142 ];

compute.roundn( data, -2 );
// returns [...] where each value is rounded to nearest hundredth
```

Note: if provided an `array`, the `array` is mutated.


<a name="polyval"></a>
#### [compute.polyval( coef, x )](https://github.com/compute-io/polynomial)

Evaluates a polynomial with coefficients `coef`, where `x` may be a single `numeric` value or an `array` of numeric values.

``` javascript
var coef = [ 4, 2, 6, -17 ];

var x = compute.polyval( coef, [ 10, -3] );
```


<a name="reverse"></a>
#### [compute.reverse( arr )](https://github.com/compute-io/reverse)

Reverses an `array` in place.

``` javascript
var arr = [ 1, 2, 3, 4 ];

compute.reverse( arr );
// returns [ 4, 3, 2, 1 ]
```

Note: the `array` is mutated.


<a name="shuffle"></a>
#### [compute.shuffle( arr )](https://github.com/compute-io/shuffle)

Generates a random permutation of (shuffles) an `array` in place.

``` javascript
var arr = [ 1, 2, 3, 4 ];

compute.shuffle( arr );
```

Note: the `array` is mutated.


<a name="circshift"></a>
#### [compute.circshift( x, k )](https://github.com/compute-io/circshift)

Circularly shifts elements/characters. `x` may be an `array` or a `string`. `k` is an `integer` specifying the number of positions to shift. The sign of `k` specifies the shift direction.

``` javascript
compute.circshift( [1,2,3,4,5], 2 );
// returns [4,5,1,2,3]

var str = compute.circshift( 'beepboop', -3 );
// returns 'pboopbee'
```

Note: if provided an `array`, the `array`, is mutated.


<a name="diff"></a>
#### [compute.diff( arr )](https://github.com/compute-io/diff)

Calculates the differences between adjacent elements in an `array`.

``` javascript
var arr = [ 2, 1, 3, 4 ];

var diff = compute.diff( arr );
// returns [ 1, -2, -1 ]
```

Note: the length of the returned `array` is one less than the length of the original `array`.


<a name="find"></a>
#### [compute.find( arr, [opts,] clbk )](https://github.com/compute-io/find)

Finds `array` elements which satisfy a test condition.

``` javascript
var arr = [ 2, 1, 3, 4 ];

var opts = {
	'k': -2,
	'returns': '*'
};

function condition( val ) {
	return val < 4;
}

var results = compute.find( arr, opts, condition );
// returns [ [2,3], [1,1] ]
```

For further documentation, see the [compute-find](https://github.com/compute-io/find) module.


<a name="deg2rad"></a>
#### [compute.deg2rad( x )](https://github.com/compute-io/deg2rad)

Converts degrees to radians, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var val = compute.deg2rad( 90 );
// returns pi/2

var data = [ 0, 45, 90, 135, 180 ];
compute.deg2rad( data );
// returns [ 0, pi/4, pi/2, 3pi/4, pi ]
```

Note: mutates the input `array`.


<a name="rad2deg"></a>
#### [compute.rad2deg( x )](https://github.com/compute-io/rad2deg)

Converts radians to degrees, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var val = compute.rad2deg( Math.PI/2 );
// returns 90

var data = [ 0, Math.PI/4, Math.PI/2, 3*Math.PI/4, Math.PI ];
compute.rad2deg( data );
// returns [ 0, 45, 90, 135, 180 ]
```

Note: mutates the input `array`.


<a name="issorted"></a>
#### [compute.issorted( arr[, comparator] )](https://github.com/compute-io/issorted)

Returns a `boolean` indicating if an input `array` is sorted.

``` javascript
var bool = compute.issorted( [ 2, 3, 5, 4 ] );
// returns false
```

By default, the method assumes __ascending__ order. To impose an arbitrary sort order, provide a `comparator` function.

``` javascript
function descending( a, b ) {
	return b - a;
}

var bool = compute.issorted( [ 5, 4, 3, 2 ] );
// returns true
```

<a name="isnan"></a>
#### [compute.isnan( arr )](https://github.com/compute-io/issorted)

Computes for each `array` element whether an element is `NaN`. The function returns an `array` with length equal to that of the input `array`. Each output `array` element is either `0` or `1`. A value of `1` means that an element is `NaN` and `0` means that an element is __not__ `NaN`.

``` javascript
var out = compute.isnan( [ 2, '3', 5, 4, null ] );
// returns [ 0, 1, 0, 0, 1 ]
```


### Special Functions

<a name="abs"></a>
#### [compute.abs( arr )](https://github.com/compute-io/abs)

Computes an element-wise absolute value for each element of a numeric `array`.

``` javascript
var data = [ 2, -4, 2, -7, 3 ];

compute.abs( data );
```

Note: mutates the input `array`.


<a name="sqrt"></a>
#### [compute.sqrt( arr )](https://github.com/compute-io/sqrt)

Computes an element-wise principal square root for each element of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.sqrt( data );
```

Note: mutates the input `array`.


<a name="signum"></a>
#### [compute.signum( x )](https://github.com/compute-io/signum)

Evaluates the signum function, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var data = [ -10, -1, -0, 0, 1, 10 ];

var x = compute.signum( data );
```

<a name="erf"></a>
#### [compute.erf( x )](https://github.com/compute-io/erf)

Evaluates the error function, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var data = [ -10, -1, 0, 1, 10 ];

var x = compute.erf( data );
```


<a name="erfc"></a>
#### [compute.erfc( x )](https://github.com/compute-io/erfc)

Evaluates the complementary error function, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var data = [ -10, -1, 0, 1, 10 ];

var x = compute.erfc( data );
```

<a name="erfinv"></a>
#### [compute.erfinv( x )](https://github.com/compute-io/erfinv)

Evaluates the inverse error function, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var data = [ -1, -0.5, 0, 0.5, 1 ];

var x = compute.erfinv( data );
```


<a name="erfcinv"></a>
#### [compute.erfcinv( x )](https://github.com/compute-io/erfcinv)

Evaluates the inverse complementary error function, where `x` may be a single `numeric` value or a numeric `array`.

``` javascript
var data = [ 0, 0.5, 1, 1.5, 2 ];

var x = compute.erfcinv( data );
```


### Arithmetic


<a name="add"></a>
#### [compute.add( arr, x )](https://github.com/compute-io/add)

Computes an element-wise addition of a numeric `array`, where `x` may be an `array` of equal length or a `numeric` value.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.add( data, 5.5 );
```

Note: mutates the input `array`.


<a name="subtract"></a>
#### [compute.subtract( arr, x )](https://github.com/compute-io/subtract)

Computes an element-wise subtraction of a numeric `array`, where `x` may be an `array` of equal length or a `numeric` value.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.subtract( data, 5.5 );
```

Note: mutates the input `array`.


<a name="multiply"></a>
#### [compute.multiply( arr, x )](https://github.com/compute-io/multiply)

Computes an element-wise multiplication of a numeric `array`, where `x` may be an `array` of equal length or a `numeric` value.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.multiply( data, 5.5 );
```

Note: mutates the input `array`.

<a name="divide"></a>
#### [compute.divide( arr, x )](https://github.com/compute-io/divide)

Computes an element-wise division of a numeric `array`, where `x` may be an `array` of equal length or a `numeric` value.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.divide( data, 5.5 );
```

Note: mutates the input `array`.


### Sets

<a name="unique"></a>
#### [compute.unique( arr[, sorted] )](https://github.com/compute-io/unique)

Removes duplicate values to determine the subset containing all unique values of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

compute.unique( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` flag to `true`.

Note: mutates the input `array`.



### Linear Algebra

<a name="l1norm"></a>
#### [compute.l1norm( arr )](https://github.com/compute-io/l1norm)

Computes the _L1_ norm (Manhattan/Taxicab norm) of an `array` of values.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var norm = compute.l1norm( data );
```

<a name="l2norm"></a>
#### [compute.l2norm( arr )](https://github.com/compute-io/l2norm)

Computes the _L2_ norm (Euclidean norm) of an `array` of values.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var norm = compute.l2norm( data );
```


<a name="linfnorm"></a>
#### [compute.linfnorm( arr )](https://github.com/compute-io/linfnorm)

Computes the infinity norm (Chebyshev/maximum/supremum/uniform norm) of an `array` of values.

``` javascript
var data = [ 2, 4, 2, -7, 3 ];

var norm = compute.linfnorm( data );
```

<a name="lpnorm"></a>
#### [compute.lpnorm( arr[, p] )](https://github.com/compute-io/lpnorm)

Computes the _Lp_ norm of an `array` of values.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

// Compute the L5 norm:
var norm = compute.lpnorm( data, 5 );
```


<a name="dot"></a>
#### [compute.dot( x, y )](https://github.com/compute-io/dot)

Computes the dot product between two `arrays` of equal length.

``` javascript
var val = compute.dot( [1,2,3], [4,5,6] );
```


<a name="cross"></a>
#### [compute.cross( x, y )](https://github.com/compute-io/cross)

Computes the cross product between two `arrays` of length `3`.

``` javascript
var val = compute.cross( [1,2,3], [4,5,6] );
```


### Statistics

<a name="min"></a>
#### [compute.min( arr )](https://github.com/compute-io/min)

Computes the minimum value of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var min = compute.min( data );
```

<a name="incrmin"></a>
#### [compute.incrmin()](https://github.com/compute-io/incrmin)

Returns a method to compute a minimum value incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var min = compute.incrmin(),
	m;

for ( var i = 0; i < data.length; i++ ) {
	m = min( data[ i ] );
	console.log( m );
}
console.log( min() );
```

<a name="mmin"></a>
#### [compute.mmin( arr, window )](https://github.com/compute-io/mmin)

Computes a moving minimum over a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.mmin( data, 2 );
```


<a name="cmin"></a>
#### [compute.cmin( arr )](https://github.com/compute-io/cmin)

Computes the cumulative minimum of a numeric `array`.

``` javascript
var data = [ 7, 4, 2, 4, 3 ];

var arr = compute.cmin( data );
```


<a name="max"></a>
#### [compute.max( arr )](https://github.com/compute-io/max)

Computes the maximum value of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var max = compute.max( data );
```


<a name="incrmax"></a>
#### [compute.incrmax()](https://github.com/compute-io/incrmax)

Returns a method to compute a maximum value incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var max = compute.incrmax(),
	m;

for ( var i = 0; i < data.length; i++ ) {
	m = max( data[ i ] );
	console.log( m );
}
console.log( max() );
```

<a name="mmax"></a>
#### [compute.mmax( arr, window )](https://github.com/compute-io/mmax)

Computes a moving maximum over a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.mmax( data, 2 );
```


<a name="cmax"></a>
#### [compute.cmax( arr )](https://github.com/compute-io/cmax)

Computes the cumulative maximum of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.cmax( data );
```


<a name="range"></a>
#### [compute.range( arr )](https://github.com/compute-io/range)

Computes the arithmetic range of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var range = compute.range( data );
```


<a name="sum"></a>
#### [compute.sum( arr )](https://github.com/compute-io/sum)

Computes the sum of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var sum = compute.sum( data );
```

<a name="nansum"></a>
#### [compute.nansum( arr )](https://github.com/compute-io/nansum)

Computes the sum of an `array` ignoring any non-numeric values.

``` javascript
var data = [ 2, NaN, 4, 2, 7, NaN, 3 ];

var sum = compute.nansum( data );
```

<a name="incrsum"></a>
#### [compute.incrsum()](https://github.com/compute-io/incrsum)

Returns a method to compute a sum incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var sum = compute.incrsum(),
	s;

for ( var i = 0; i < data.length; i++ ) {
	s = sum( data[ i ] );
	console.log( s );
}
console.log( sum() );
```


<a name="msum"></a>
#### [compute.msum( arr, window )](https://github.com/compute-io/msum)

Computes a moving sum over a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.msum( data, 2 );
```


<a name="csum"></a>
#### [compute.csum( arr )](https://github.com/compute-io/csum)

Computes the cumulative sum of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.csum( data );
```


<a name="mean"></a>
#### [compute.mean( arr )](https://github.com/compute-io/mean)

Computes the arithmetic mean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mean = compute.mean( data );
```

<a name="nanmean"></a>
#### [compute.nanmean( arr )](https://github.com/compute-io/nanmean)

Computes the arithmetic mean over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var mean = compute.nanmean( data );
```


<a name="incrmean"></a>
#### [compute.incrmean()](https://github.com/compute-io/incrmean)

Returns a method to compute an arithmetic mean incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mean = compute.incrmean(),
	mu;

for ( var i = 0; i < data.length; i++ ) {
	mu = mean( data[ i ] );
	console.log( mu );
}
console.log( mean() );
```


<a name="mmean"></a>
#### [compute.mmean( arr, window )](https://github.com/compute-io/mmean)

Computes a moving arithmetic mean (sliding window average) over a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.mmean( data, 2 );
```


<a name="wmean"></a>
#### [compute.wmean( arr, weights )](https://github.com/compute-io/wmean)

Computes a weighted mean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ],
	weights = [ 1, 2, 1, 4, 0 ];

var wmean = compute.wmean( data, weights );
```

<a name="gmean"></a>
#### [compute.gmean( arr )](https://github.com/compute-io/gmean)

Computes the geometric mean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var gmean = compute.gmean( data );
```


<a name="nangmean"></a>
#### [compute.nangmean( arr )](https://github.com/compute-io/nangmean)

Computes the geometric mean over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var gmean = compute.nangmean( data );
```


<a name="hmean"></a>
#### [compute.hmean( arr )](https://github.com/compute-io/hmean)

Computes the harmonic mean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var hmean = compute.hmean( data );
```

<a name="nanhmean"></a>
#### [compute.nanhmean( arr )](https://github.com/compute-io/nanhmean)

Computes the harmonic mean over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var hmean = compute.nanhmean( data );
```


<a name="qmean"></a>
#### [compute.qmean( arr )](https://github.com/compute-io/qmean)

Computes the quadratic mean (root mean square) of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var qmean = compute.qmean( data );
```


<a name="nanqmean"></a>
#### [compute.nanqmean( arr )](https://github.com/compute-io/nanqmean)

Computes the quadratic mean (root mean square) over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var qmean = compute.nanqmean( data );
```


<a name="variance"></a>
#### [compute.variance( arr )](https://github.com/compute-io/variance)

Computes the sample variance over a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var s2 = compute.variance( data );
```


<a name="nanvariance"></a>
#### [compute.nanvariance( arr )](https://github.com/compute-io/nanvariance)

Computes the sample variance over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var s2 = compute.nanvariance( data );
```

<a name="incrvariance"></a>
#### [compute.incrvariance()](https://github.com/compute-io/incrvariance)

Returns a method to compute a sample variance incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var variance = compute.incrvariance(),
	s2;

for ( var i = 0; i < data.length; i++ ) {
	s2 = variance( data[ i ] );
	console.log( s2 );
}
console.log( variance() );
```


<a name="stdev"></a>
#### [compute.stdev( arr )](https://github.com/compute-io/stdev)

Computes the sample standard deviation of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var stdev = compute.stdev( data );
```


<a name="nanstdev"></a>
#### [compute.nanstdev( arr )](https://github.com/compute-io/nanstdev)

Computes the sample standard deviation over an `array` of values ignoring any non-numeric values.

``` javascript
var data = [ 2, 4, NaN, 2, 7, NaN, 3 ];

var stdev = compute.nanstdev( data );
```

<a name="incrstdev"></a>
#### [compute.incrstdev()](https://github.com/compute-io/incrstdev)

Returns a method to compute a sample standard deviation incrementally.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var stdev = compute.incrstdev(),
	sigma;

for ( var i = 0; i < data.length; i++ ) {
	sigma = stdev( data[ i ] );
	console.log( sigma );
}
console.log( stdev() );
```


<a name="mode"></a>
#### [compute.mode( arr )](https://github.com/compute-io/mode)

Computes the mode of an `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mode = compute.mode( data );
```


<a name="median"></a>
#### [compute.median( arr[, sorted] )](https://github.com/compute-io/median)

Computes the median of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var median = compute.median( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` flag to `true`.


<a name="quantile"></a>
#### [compute.quantile( arr, p[, opts] )](https://github.com/compute-io/quantile)

Computes a quantile for a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var q = compute.quantile( data, 0.25 );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` option to `true`.

``` javascript
var opts = {
	'sorted': true
};

var data = [ 2, 2, 3, 4, 7 ];

var q = compute.quantile( data, 0.25, opts );
```


<a name="quantiles"></a>
#### [compute.quantiles( arr, num[, opts] )](https://github.com/compute-io/quantiles)

Computes quantiles for a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var arr = compute.quantiles( data, 3 );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` option to `true`.

``` javascript
var opts = {
	'sorted': true
};

var data = [ 2, 2, 3, 4, 7 ];

var arr = compute.quantiles( data, 2, opts );
```


<a name="iqr"></a>
#### [compute.iqr( arr[, opts] )](https://github.com/compute-io/iqr)

Computes the interquartile range of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var iqr = compute.iqr( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` options flag to `true`.


<a name="idr"></a>
#### [compute.idr( arr[, opts] )](https://github.com/compute-io/idr)

Computes the interdecile range of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var idr = compute.idr( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` options flag to `true`.


<a name="midrange"></a>
#### [compute.midrange( arr[, sorted] )](https://github.com/compute-io/midrange)

Computes the mid-range (mid-extreme) of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mr = compute.midrange( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` flag to `true`.


<a name="midhinge"></a>
#### [compute.midhinge( arr[, opts] )](https://github.com/compute-io/midhinge)

Computes the midhinge of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mh = compute.midhinge( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` options flag to `true`.


<a name="midsummary"></a>
#### [compute.midsummary( arr, n[, opts] )](https://github.com/compute-io/midsummary)

Computes the *n*% midsummary of a numeric `array`. `n` exists on the interval `[0.0, 0.50]` and specifies the proportion of values to discard in the distribution tails.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var ms = compute.midsummary( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` options flag to `true`.



<a name="midmean"></a>
#### [compute.midmean( arr[, sorted] )](https://github.com/compute-io/midmean)

Computes the midmean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var mm = compute.midmean( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` flag to `true`.


<a name="trimean"></a>
#### [compute.trimean( arr[, opts] )](https://github.com/compute-io/trimean)

Computes the trimean of a numeric `array`.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var trimean = compute.trimean( data );
```

If the input `array` is already sorted in __ascending__ order, set the `sorted` options flag to `true`.



<a name="skewness"></a>
#### [compute.skewness( arr )](https://github.com/compute-io/skewness)

Computes the sample skewness of an `array` of values.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var skew = compute.skewness( data );
```


<a name="kurtosis"></a>
#### [compute.kurtosis( arr )](https://github.com/compute-io/kurtosis)

Computes the sample excess kurtosis of an `array` of values.

``` javascript
var data = [ 2, 4, 2, 7, 3 ];

var kur = compute.kurtosis( data );
```



### Geometry

<a name="hypot"></a>
#### [compute.hypot( a, b )](https://github.com/compute-io/hypot)

Computes the hypotenuse of a right triangle.

``` javascript
var a = 10,
	b = 12;

var c = compute.hypot( a, b );
```


### Information Theory

<a name="hamdist"></a>
#### [compute.hamdist( a, b )](https://github.com/compute-io/hamming)

Computes the [Hamming distance](http://en.wikipedia.org/wiki/Hamming_distance) between two sequences of equal length.

``` javascript
var a = 'beep',
	b = 'boop';

var dist = compute.hamdist( a, b );

var c = [ 4, 2, 3, 4 ],
	d = [ 2, 4, 3, 1 ];

var dist = compute.hamdist( c, d );
```



## Fluent Interface

For data pipelines, invoking serial methods can become verbose.

``` javascript
data = compute.roundn( data, -3 );
data = compute.mean( data );
data = compute.roundn( data, 0 );
...
```

[Fluent](http://en.wikipedia.org/wiki/Fluent_interface) interfaces can help alleviate this problem. Such interfaces have been popularized by libraries such as [jQuery](http://jquery.com) and [D3](http://d3js.org) which utilize method chaining.

To create a fluent interface,

``` javascript
var flow = compute.flow();
```

A `flow` pipeline should be initialized.

``` javascript
flow.value( data );
```

Once initialized, all compute methods are now available. The lone difference is that data should __not__ be explicitly passed as an argument. For example,

``` javascript
flow
	.value( data )
	.roundn( -3 )
	.mean()
	.roundn( 0 );
```

To return the flow `value`,

``` javascript
var mean = flow.value();
```

To help understand the transformations comprising a data pipeline, `flow` exposes an `inspect()` method, which logs the current `value` to the console while maintaining the fluent interface.

``` javascript
flow.inspect();
```

The above `flow` can be modified accordingly,

``` javascript
flow
	.value( data )
	.inspect()
	.roundn( -3 )
	.inspect()
	.mean()
	.inspect()
	.roundn( 0 )
	.inspect();
```

To summarize the `flow` API...

#### flow.value( [value] )

This method is a setter/getter. If no `value` is provided, returns the current flow `value`. If a `value` is provided, sets the flow `value`.

``` javascript
flow.value( [ 4, 3, 6, 2 ] );
```


#### flow.inspect()

Logs the current flow `value` to the console, while maintaining the fluent interface.

``` javascript
flow.inspect();
```


## Notes

1. 	When creating flows, ensure that the output from one computation matches the input argument requirements for the next computation.
2. 	For large datasets, rather than loading datasets into memory, consider using file streams and utilize stream tools such as [Flow.io](https://github.com/flow-io/flow.io).


## Tests

### Unit

Unit tests use the [Mocha](http://visionmedia.github.io/mocha) test framework with [Chai](http://chaijs.com) assertions. To run the tests, execute the following command in the top-level application directory:

``` bash
$ make test
```

All new feature development should have corresponding unit tests to validate correct functionality.


### Test Coverage

This repository uses [Istanbul](https://github.com/gotwarlost/istanbul) as its code coverage tool. To generate a test coverage report, execute the following command in the top-level application directory:

``` bash
$ make test-cov
```

Istanbul creates a `./reports/coverage` directory. To access an HTML version of the report,

``` bash
$ make view-cov
```


## License

[MIT license](http://opensource.org/licenses/MIT). 


---
## Copyright

Copyright &copy; 2014. Athan Reines.



[npm-image]: http://img.shields.io/npm/v/compute.io.svg
[npm-url]: https://npmjs.org/package/compute.io

[travis-image]: http://img.shields.io/travis/compute-io/compute.io/master.svg
[travis-url]: https://travis-ci.org/compute-io/compute.io

[coveralls-image]: https://img.shields.io/coveralls/compute-io/compute.io/master.svg
[coveralls-url]: https://coveralls.io/r/compute-io/compute.io?branch=master

[dependencies-image]: http://img.shields.io/david/compute-io/compute.io.svg
[dependencies-url]: https://david-dm.org/compute-io/compute.io

[dev-dependencies-image]: http://img.shields.io/david/dev/compute-io/compute.io.svg
[dev-dependencies-url]: https://david-dm.org/dev/compute-io/compute.io

[github-issues-image]: http://img.shields.io/github/issues/compute-io/compute.io.svg
[github-issues-url]: https://github.com/compute-io/compute.io/issues
