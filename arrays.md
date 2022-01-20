# Arrays

Array: ordered collection of values (elements) with a numeric position (index), and with a length property.  
Arrays are untyped, zero-based, dinamic and may be sparse. Inherit properties from Array.prototype (most of these methods are generic: also work with array-like objects).   

### Creating arrays.  

- Array Literals

        let empty = [];
        let primes = [2, 3, 5, 7, 11];

- The Array Constructor

        let a = new Array();
        let a = new Array(10);  // an array with length = 10
        let a = new Array(5, 4, 3, 2, 1);

- The Spread Operator

        let a = [1, 2, 3];
        let b = [0, ...a, 4];   // b = [0, 1, 2, 3, 4]

        a convenient way to create a copy of an array, and an easy way to remove duplicate elements

        let letters = [..."hello world"];
        [...new Set(letters)]

- Array.of()

        Array.of()      // => []
        Array.of(10)    // => [10]

- Array.from()

        let truearray = Array.from(arraylike);

### Reading and writing array elements

Using the [] operator after the array name, with a non negative integer.

### Sparse array
Array in which the elements do not have contiguous indexes.

### Length
length = number of elements = highest index + 1

### Methods

    [[Prototype]]: Array(0)
    at: ƒ at()
    concat: ƒ concat()
    constructor: ƒ Array()
    copyWithin: ƒ copyWithin()
    entries: ƒ entries()
    every: ƒ every()
    fill: ƒ fill()
    filter: ƒ filter()
    find: ƒ find()
    findIndex: ƒ findIndex()
    findLast: ƒ findLast()
    findLastIndex: ƒ findLastIndex()
    flat: ƒ flat()
    flatMap: ƒ flatMap()
    forEach: ƒ forEach()
    from: ƒ from()
    includes: ƒ includes()
    indexOf: ƒ indexOf()
    isArray: ƒ isArray()
    join: ƒ join()
    keys: ƒ keys()
    lastIndexOf: ƒ lastIndexOf()
    length: 0
    map: ƒ map()
    of: ƒ of()
    pop: ƒ pop()
    push: ƒ push()
    reduce: ƒ reduce()
    reduceRight: ƒ reduceRight()
    reverse: ƒ reverse()
    shift: ƒ shift()
    slice: ƒ slice()
    some: ƒ some()
    sort: ƒ sort()
    splice: ƒ splice()
    toLocaleString: ƒ toLocaleString()
    toString: ƒ toString()
    unshift: ƒ unshift()
    values: ƒ values()
    Symbol(Symbol.iterator): ƒ values()
    Symbol(Symbol.unscopables): {copyWithin: true, entries: true, fill: true, find: true, findIndex: true, …}
    [[Prototype]]: Object

### push()
Adds one or more elements to the end of an array and returns the new length of the array.

    arr.push(element);

### unshift()
Adds one or more elements to the beginning of an array and returns the new length of the array.

    arr.unshift(element);

### pop()
Deletes the last element of an array, decrements the array length and returns the value that it removed.

    arr.pop();

### shift()
Removes and returns the first element of aan array, decrementing the array length.

    arr.shift();

### indexOf()
Searches an array for an element with a specified value and returns the index of the first element found, or -1 if none is found. It uses strict equality (===).
Optional 2nd argument: index at which to begin the search.

    let a = [0, 1, 2, 3, 4];
    a.indexOf(2);               //=> 2

### lastIndexOf()
The same as indexOf() but searching the array from end to beginning.

### includes()
Takes a single argument and returns true if the array contains that value or false otherwise. It uses strict equality (===).

    arr.includes(valueToFind);

### sort()
Sorts the elements of an array in place and returns the sorted array. With no arguments, it sorts the array elements in alphabetical order.

    arr.sort();

To sort into numerical rather than alphabetical order, you must pass a comparison function:

    let a = [33, 4, 111, 222];
    a.sort();                       // a == [1111, 222, 33, 4]
    a.sort((a, b) => a - b);        // a == [4, 33, 222, 1111]
    a.sort((a, b) => b - a);        // a == [1111, 222, 33, 4]

Case-insensitive alphabetical sort:

    a.sort((s, t) => {
        let a = s.toLowerCase();
        let b = t.toLowerCase();
        if (a < b) return -1;
        if (a > b) return 1;
        return 0;
    });

### reverse()
Reverses in place the order of the elements of an array and returns the reversed array.

    arr.reverse();

### concat()
Used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

    arr1.concat(arr2)       // same as [...arr1, ...arr2];

### join()
Converts all the elements of an array to strings and concatenates them, separated by commas (default) or a specified separator string, returning the resulting string. It is the inverse of the String.split() method.

    arr.join(separator);    // optional: ('-')

### toString()
It works just like the join() method with no arguments.

    arr.toString();

### toLocaleString()
The same as toString() but using locale settings.

    arr.toLocaleString(locales);    // locales = a string with a BCP 47 language tag

### slice()
Returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included). The original array will not be modified.

    arr.slice(start, end);      // if end is a negative number, then relative to the
                                // length of the array
    arr.slice(-1);              // ideal to extract last element
    arr.slice();                // to create a shallow copy = [...arr];

### splice()
Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place. Original array will be modified.

    arr.splice(start, deleteCount, item1...);
        // start: index at which to start changing the array
        // deleteCount: number of elements to remove from start
        // item1: (optional) elements to add to the array from start

### fill()
Changes all elements in an array to a static value, from a start index (default to 0) to an end index (default length). It returns the modified array.

    arr.fill(value, start, end);    // start and end are optional indexes

### copyWithin()
Copies a slice of an array to a new position within the array.

    arr.copyWithin(target, start, end);
        // target: destination index to which the first element will be copied
        // start: (optional) index of the first element to be copied
        // end: (optional) end of the slice of elements to be copied

### forEach()
Executes a provided function once for each array element.

    arr.forEach(callback(currentValue, index, array) {
        execute something;
    });
        // index and array are optionals

There is no way to stop or break a forEach() loop.

    let data = [1, 2, 3, 4], sum = 0;
    function adder(number) {
        sum += number;
    }
    data.forEach(adder);

### map()
Passes each element of the array to the function you specify and returns an array containing the values returned by your function.

    let newArray = arr.map(callback(currentValue, index, array) {
        // return element for newArray, after executing something
    });
    // index and array are optionals

### filter()
Creates a new array with all elements that pass the test implemented by the provided function.

    let newArray = arr.filter(callback(currentValue, index, array) {
        // return element for newArray, if true
    });
    // index and array are optionals

### reduce()
Combines the elements of an array, using the function you specify, to produce a single value.

    let newArray = arr.reduce(callback(currentValue, index, array) {
        // return
    } initialValue);
    // index and array are optionals
    // initialValue is optional. If omited it uses the first element of the array

### reduceRight()
It works like reduce(), except that it processes the array from highest index to lowest.