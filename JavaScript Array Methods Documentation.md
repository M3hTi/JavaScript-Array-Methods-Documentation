# JavaScript Array Methods Documentation

## Table of Contents
1. [Basic Array Operations](#basic-array-operations)
2. [Array Manipulation Methods](#array-manipulation-methods)
3. [Ordering Methods](#ordering-methods)
4. [Extraction and Insertion Methods](#extraction-and-insertion-methods)
5. [Stack Operations (LIFO)](#stack-operations-lifo)
6. [Queue Operations (FIFO)](#queue-operations-fifo)
7. [Array Iteration Methods](#array-iteration-methods)
8. [Search Methods](#search-methods)
9. [Important Notes](#important-notes)

## Basic Array Operations
Arrays in JavaScript are ordered collections that can hold any type of data. Array indices start at 0.

```javascript
// Creating an array
let fruits = ["apple", "banana", "orange"];

// Accessing elements
console.log(fruits[0]); // "apple"

// Getting array length
console.log(fruits.length); // 3
```

## Array Manipulation Methods

### `copyWithin(target, start, end)`
Copies a sequence of array elements within the array.
```javascript
let array = ['a', 'b', 'c', 'd', 'e'];
array.copyWithin(0, 3, 4);  // ['d', 'b', 'c', 'd', 'e']
// Copies from index 3 to 4 (exclusive) and pastes starting at index 0

// More examples
let numbers = [1, 2, 3, 4, 5];
numbers.copyWithin(2, 0, 2);  // [1, 2, 1, 2, 5]
```

### `concat(array1, array2, ...)`
Joins two or more arrays and returns a new array.
```javascript
let arr1 = [1, 2];
let arr2 = [3, 4];
let arr3 = [5, 6];
let combined = arr1.concat(arr2, arr3); // [1, 2, 3, 4, 5, 6]

// Can also concatenate values
let newArr = arr1.concat('a', ['b', 'c']); // [1, 2, 'a', 'b', 'c']
```

### `fill(value, start, end)`
Fills array elements with a static value from start to end index.
```javascript
let array = [1, 2, 3, 4, 5];
array.fill(0, 1, 4); // [1, 0, 0, 0, 5]

// Fill entire array
let zeros = new Array(3).fill(0); // [0, 0, 0]

// Fill from index to end
let numbers = [1, 2, 3, 4];
numbers.fill(9, 2); // [1, 2, 9, 9]
```

### `indexOf(value, start)`
Returns the first index of an element in the array, -1 if not found.
```javascript
let fruits = ['apple', 'banana', 'apple', 'orange'];
console.log(fruits.indexOf('apple')); // 0
console.log(fruits.indexOf('apple', 1)); // 2
console.log(fruits.indexOf('mango')); // -1
```

### `join(separator)`
Converts array to a string with elements separated by the specified separator.
```javascript
let elements = ['Fire', 'Air', 'Water'];
console.log(elements.join()); // "Fire,Air,Water"
console.log(elements.join('-')); // "Fire-Air-Water"
console.log(elements.join('')); // "FireAirWater"
```

### `lastIndexOf(value, start)`
Searches array backwards and returns the last index of an element, -1 if not found.
```javascript
let numbers = [1, 2, 3, 2, 1];
console.log(numbers.lastIndexOf(2)); // 3
console.log(numbers.lastIndexOf(2, 2)); // 1
console.log(numbers.lastIndexOf(4)); // -1
```

### `toString()`
Converts array to a string with comma-separated values.
```javascript
let array = [1, 2, 'a', '1a'];
console.log(array.toString()); // "1,2,a,1a"

// Difference from join()
let arr = [1, 2, 3];
console.log(arr.toString()); // "1,2,3"
console.log(arr.join()); // "1,2,3"
```

## Ordering Methods

### `reverse()`
Reverses the order of array elements.
```javascript
let cards = ["Ace", "King", "Queen", "Jack"];
cards.reverse(); // returns ["Jack", "Queen", "King", "Ace"]
```

### `sort()`
Sorts array elements with special consideration needed for numbers.

**String Sorting:**
```javascript
let cards = ["Ace", "King", "Queen", "Jack"];
cards.sort(); // returns ["Ace", "Jack", "King", "Queen"]
```

**Numeric Sorting:**
```javascript
// Without comparison function (incorrect for numbers)
let numbers = [1, 30, 4, 21, 100000];
numbers.sort(); // returns [1, 100000, 21, 30, 4] (incorrect!)

// Ascending order (correct)
numbers.sort((a, b) => a - b); // returns [1, 4, 21, 30, 100000]

// Descending order
numbers.sort((a, b) => b - a); // returns [100000, 30, 21, 4, 1]
```

## Extraction and Insertion Methods

### `slice(start, stop)`
Extracts a portion of an array without modifying the original array.
```javascript
let months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
let summerMonths = months.slice(5, 8); // returns ["Jun", "Jul", "Aug"]
```

### `splice(start, size, values)`
Removes and/or inserts elements into an array, modifying the original array.
```javascript
let emp = ["Drew", "Lee", "Grant", "Li", "Rao", "Yang"];
emp.splice(1, 3, "Evans", "Greer", "Smith");
// emp = ["Drew", "Evans", "Greer", "Smith", "Rao", "Yang"]
```

## Stack Operations (LIFO)

### `push(values)`
Adds elements to the end of an array.
```javascript
let x = ["a", "b", "c"];
x.push("d", "e"); // x = ["a", "b", "c", "d", "e"]
```

### `pop()`
Removes and returns the last element.
```javascript
let x = ["a", "b", "c", "d", "e"];
x.pop(); // returns "e", x = ["a", "b", "c", "d"]
```

## Queue Operations (FIFO)

### `shift()`
Removes and returns the first element.
```javascript
let x = ["a", "b", "c", "d"];
x.shift(); // returns "a", x = ["b", "c", "d"]
```

### `unshift(values)`
Adds elements to the beginning of an array.
```javascript
let x = ["c", "d", "e"];
x.unshift("a", "b"); // x = ["a", "b", "c", "d", "e"]
```

## Array Iteration Methods

### `every(callback, thisArg)`
Tests if all elements pass the test implemented by the callback function.
```javascript
let numbers = [2, 4, 6, 8];
let allEven = numbers.every(num => num % 2 === 0); // returns true

numbers.every((num, index, array) => {
    console.log(`Checking element ${num} at index ${index}`);
    return num % 2 === 0;
});
```

### `filter(callback, thisArg)`
Creates a new array with elements that pass the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let evenNumbers = numbers.filter(num => num % 2 === 0); // returns [2, 4]

// With objects
let people = [
    { name: "John", age: 30 },
    { name: "Jane", age: 15 }
];
let adults = people.filter(person => person.age >= 18);
```

### `forEach(callback, thisArg)`
Executes a function once for each array element.
```javascript
let fruits = ["apple", "banana", "cherry"];
fruits.forEach((fruit, index) => {
    console.log(`Fruit ${index + 1}: ${fruit}`);
});
```

### `map(callback, thisArg)`
Creates a new array with the results of calling the callback on every element.
```javascript
let numbers = [1, 2, 3];
let doubled = numbers.map(num => num * 2); // returns [2, 4, 6]

// With objects
let users = [
    { name: "John", age: 30 },
    { name: "Jane", age: 25 }
];
let names = users.map(user => user.name); // returns ["John", "Jane"]
```

### `reduce(callback, thisArg)`
Reduces the array to a single value (from left to right).
```javascript
let numbers = [1, 2, 3, 4];
let sum = numbers.reduce((acc, curr) => acc + curr); // returns 10

// With initial value
let sum2 = numbers.reduce((acc, curr) => acc + curr, 0);

// Creating an object
let fruits = ["apple", "banana", "apple", "cherry", "banana"];
let count = fruits.reduce((acc, fruit) => {
    acc[fruit] = (acc[fruit] || 0) + 1;
    return acc;
}, {});
```

### `reduceRight(callback, thisArg)`
Reduces the array to a single value (from right to left).
```javascript
let numbers = [1, 2, 3, 4];
let result = numbers.reduceRight((acc, curr) => acc - curr); // 4-3-2-1
```

## Search Methods

### `some(callback, thisArg)`
Tests whether at least one element passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let hasEven = numbers.some(num => num % 2 === 0); // returns true

let users = [
    { name: "John", active: true },
    { name: "Jane", active: false }
];
let hasActiveUser = users.some(user => user.active); // returns true
```

### `find(callback, thisArg)`
Returns the first element that passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let firstEven = numbers.find(num => num % 2 === 0); // returns 2

let users = [
    { id: 1, name: "John" },
    { id: 2, name: "Jane" }
];
let user = users.find(user => user.id === 2); // returns { id: 2, name: "Jane" }
```

### `findIndex(callback, thisArg)`
Returns the index of the first element that passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let firstEvenIndex = numbers.findIndex(num => num % 2 === 0); // returns 1

let users = [
    { id: 1, name: "John" },
    { id: 2, name: "Jane" }
];
let janeIndex = users.findIndex(user => user.name === "Jane"); // returns 1
```

## Important Notes

### Method Categories
- **Mutating Methods** (modify the original array):
  - `copyWithin()`, `fill()`, `push()`, `pop()`, `shift()`
  - `unshift()`, `reverse()`, `sort()`, `splice()`
  
- **Non-mutating Methods** (return new array/value):
  - `concat()`, `indexOf()`, `lastIndexOf()`, `join()`
  - `toString()`, `slice()`, `map()`, `filter()`
  - `reduce()`, `reduceRight()`, `find()`, `findIndex()`

### Parameter Types
- **Callback Functions** receive three arguments:
  - `element`: Current element being processed
  - `index`: Index of current element
  - `array`: The array being traversed
  
- **thisArg** (optional):
  - Sets the `this` value for callback function execution

### Common Gotchas
1. `sort()` converts elements to strings by default
2. `indexOf()` uses strict equality (`===`)
3. Negative indices count from end of array
4. Most iteration methods skip empty elements
5. Chaining methods may impact performance