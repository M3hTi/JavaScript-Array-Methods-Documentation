# JavaScript Array Methods Documentation

## Table of Contents
1. [Basic Array Operations](#basic-array-operations)
2. [Ordering Methods](#ordering-methods)
3. [Extraction and Insertion Methods](#extraction-and-insertion-methods)
4. [Stack Operations (LIFO)](#stack-operations-lifo)
5. [Queue Operations (FIFO)](#queue-operations-fifo)
6. [Array Iteration Methods](#array-iteration-methods)
7. [Search Methods](#search-methods)

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

**Sorting Objects:**
```javascript
let items = [
  { name: "Book", price: 30 },
  { name: "Pen", price: 2 },
  { name: "Desk", price: 150 }
];

// Sort by price ascending
items.sort((a, b) => a.price - b.price);
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

// With index and array parameters
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

// With more complex conditions
let people = [
    { name: "John", age: 30 },
    { name: "Jane", age: 15 },
    { name: "Bob", age: 25 }
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

// Transforming objects
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

// Creating an object from array
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

// Checking for specific conditions
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

// Finding objects
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

// Working with objects
let users = [
    { id: 1, name: "John" },
    { id: 2, name: "Jane" }
];
let janeIndex = users.findIndex(user => user.name === "Jane"); // returns 1
```

## Notes
- All methods that accept a callback function provide three arguments to the callback:
  - `element`: The current element being processed
  - `index`: The index of the current element
  - `array`: The array being traversed
- `thisArg` is an optional parameter that sets the `this` value for the callback function
- Methods like `map`, `filter`, and `reduce` create new arrays without modifying the original
- Methods like `push`, `pop`, `shift`, `unshift`, and `splice` modify the original array
- Array indices are zero-based
- The `sort` method modifies the original array