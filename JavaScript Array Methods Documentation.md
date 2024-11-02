# JavaScript Array Methods Documentation

## Basic Array Operations

### Ordering Methods

#### `reverse()`
Reverses the order of array elements.
```javascript
let cards = ["Ace", "King", "Queen", "Jack"];
cards.reverse(); // returns ["Jack", "Queen", "King", "Ace"]
```

#### `sort()`
Rearranges array elements in lexicographical order.
```javascript
let cards = ["Ace", "King", "Queen", "Jack"];
cards.sort(); // returns ["Ace", "Jack", "King", "Queen"]
```

### Extraction and Insertion Methods

#### `slice(start, stop)`
Extracts a portion of an array without modifying the original array.
- `start`: Index where extraction begins
- `stop` (optional): Index before which extraction ends
```javascript
let months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"];
let summerMonths = months.slice(5, 8); // returns ["Jun", "Jul", "Aug"]
```

#### `splice(start, size, values)`
Removes and/or inserts elements into an array, modifying the original array.
- `start`: Starting index
- `size`: Number of elements to remove
- `values` (optional): Elements to insert
```javascript
let emp = ["Drew", "Lee", "Grant", "Li", "Rao", "Yang"];
emp.splice(1, 3, "Evans", "Greer", "Smith");
// emp = ["Drew", "Evans", "Greer", "Smith", "Rao", "Yang"]
```

### Stack Operations (LIFO)

#### `push(values)`
Adds elements to the end of an array.
```javascript
let x = ["a", "b", "c"];
x.push("d", "e"); // x = ["a", "b", "c", "d", "e"]
```

#### `pop()`
Removes and returns the last element.
```javascript
let x = ["a", "b", "c", "d", "e"];
x.pop(); // returns "e", x = ["a", "b", "c", "d"]
```

### Queue Operations (FIFO)

#### `shift()`
Removes and returns the first element.
```javascript
let x = ["a", "b", "c", "d"];
x.shift(); // returns "a", x = ["b", "c", "d"]
```

#### `unshift(values)`
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
```

### `filter(callback, thisArg)`
Creates a new array with elements that pass the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let evenNumbers = numbers.filter(num => num % 2 === 0); // returns [2, 4]
```

### `forEach(callback, thisArg)`
Executes a function once for each array element.
```javascript
let fruits = ["apple", "banana", "cherry"];
fruits.forEach(fruit => console.log(fruit));
```

### `map(callback, thisArg)`
Creates a new array with the results of calling the callback on every element.
```javascript
let numbers = [1, 2, 3];
let doubled = numbers.map(num => num * 2); // returns [2, 4, 6]
```

### `reduce(callback, thisArg)`
Reduces the array to a single value (from left to right).
```javascript
let numbers = [1, 2, 3, 4];
let sum = numbers.reduce((acc, curr) => acc + curr); // returns 10
```

### `reduceRight(callback, thisArg)`
Reduces the array to a single value (from right to left).
```javascript
let numbers = [1, 2, 3, 4];
let result = numbers.reduceRight((acc, curr) => acc - curr); // 4-3-2-1
```

### Search Methods

#### `some(callback, thisArg)`
Tests whether at least one element passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let hasEven = numbers.some(num => num % 2 === 0); // returns true
```

#### `find(callback, thisArg)`
Returns the first element that passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let firstEven = numbers.find(num => num % 2 === 0); // returns 2
```

#### `findIndex(callback, thisArg)`
Returns the index of the first element that passes the test implemented by the callback.
```javascript
let numbers = [1, 2, 3, 4, 5];
let firstEvenIndex = numbers.findIndex(num => num % 2 === 0); // returns 1
```

## Notes
- `thisArg` is an optional parameter that can be used to set the `this` value for the callback function
- Callback functions typically receive three arguments:
  - Current element being processed
  - Index of the current element
  - The array being traversed