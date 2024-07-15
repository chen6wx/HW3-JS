# Homework 3: Javascript

## Explain what is prototype and what is prototype chain in your own words

A prototype is an object that other objects inherit from. A prototype chain is where objects check it's prototype for the method or property until it finds them or reaches the end.

## Implement your versions of the following Array methods (choose 6)

map, filter, reduce, every, find, includes, join, pop, push, reverse, slice, sort

### map

```javascript
Array.prototype.myMap = function(callbackFn, thisArg) {
    if (thisArg) {
        callbackFn = callbackFn.bind(thisArg);
    }
    let newArray = [];
    for (let i = 0; i < this.length; i++) {
        newArray.push(callbackFn(this[i], i, this));
    }
    return newArray;
}
```

### filter

```javascript
Array.prototype.myFilter = function(callbackFn, thisArg) {
    if (thisArg) {
        callbackFn = callbackFn.bind(thisArg);
    }
    let newArray = [];
    for (let i = 0; i < this.length; i) {
        if callbackFn(this[i], i, this) {
            newArray.push(this[i]);
        }
    }
    return newArray;
}
```

### reduce

```javascript
Array.prototype.myReduce = function(callbackFn, initialValue) {
    let accumulator = this[0];
    let startIndex = 1;
    if (initialValue) {
        accumulator = initialValue;
        startIndex = 0;
    }
    for (let i = startIndex; i < this.length; i++) {
        accumulator = callbackFn(accumulator, this[i], i , this);
    }
    return accumulator;
}
```

### every

```javascript
Array.prototype.myEvery = function(callbackFn, thisArg) {
    if (thisArg) {
        callbackFn = callbackFn.bind(thisArg);
    }
    for (let i = 0; i < this.length; i++) {
        if (!callbackFn(this[i], i, this)) {
            return false;
        }
    }
    return true;
}
```

### find

```javascript
Array.prototype.myFind = function(callbackFn, thisArg) {
    if (thisArg) {
        callbackFn = callbackFn.bind(thisArg);
    }
    for (let i = 0; i < this.length; i++) {
        if (callbackFn(this[i], i, this)) {
            return this[i];
        }
    }
    return undefined;
}
```

### includes

```javascript
Array.prototype.myIncludes = function(searchElement, fromIndex) {
    startIndex = 0;
    if (fromIndex) {
        startIndex = fromIndex;
    }
    for (let i = startIndex; i < this.length; i) {
        if (this[i] === searchElement) {
            return true;
        }
    }
    return false;
}
