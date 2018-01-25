# Syntax Changes/Extensions

6. Let & Block Scope

7. Constants with "const"

Array and Object are reference type, when declare const array=[1,2,3] or const obj = { name: "robin"}, later we updated the value, there is no error, because it doesn't change the pointer of the reference

```javascript
const array = [1,2,3]
console.log(array) // [1,2,3]
array.push([4])
console.log(array) // [1,2,3,4]
```

8. Hoisting in ES6 ***

Declare things before it's being used..

* [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
* [JavaScript Hoisting](https://www.w3schools.com/js/js_hoisting.asp)
* [什么是Javascript Hoisting](http://web.jobbole.com/84055/)

9. (Fat) Arrow functions

```javascript
var fn = (a, b) => a + b;

function fn(a, b) {
  return a + b;
}

var fn = a => a + 5; // the only case that we can remove the ()
```

10. (Fat) Arrow functions and the "this" keyword

```javascript
// "this" will change depends on where you used this function
function fn() {
  console.log(this)
}

// Very important, arrow function keeps it's context where it's defined,
// no matter how or where you called this function
var fn2 = () => console.log(this)
```

11. Functions and default parameters

```javascript
// case 1
function isEqualTo(number = 10, compare) {
  return number == compare
}
console.log(isEqualTo(10))     // false
console.log(isEqualTo(11))     // false
console.log(isEqualTo(10, 10)) // true

// case 2
function isEqualTo(number, compare = number) {
  return number == compare
}
console.log(isEqualTo(10))     // true
console.log(isEqualTo(11, 20)) // false

// case 3
let a = 100
function isEqualTo(number, compare = a) {
  return number == compare
}
console.log(isEqualTo(10))     // false
```

12. Object Literal Extensions

```javascript
// case 1
let age = 25;
let obj = {
  "name": 'Max',
  age,
  "greet me"() {
     console.log(this.name + ", " + this.age)
  }
}
obj["greet me"](); // "Max, 25"

// case 2
let ageField = "age"
let obj = {
  "name": 'Max',
  [ageField]: 28, // dynamic field in object
  "greet me"() {
     console.log(this.name + ", " + this.age)
  }
}
obj["greet me"]();  // "Max, 28"
console.log( obj[ageField] ) // 28
```

13. The Rest Operator

```javascript
function sumUp(...toAdd) {
  let result = 0
  for(let i=0; i < toAdd.length; i++) {
    result += toAdd[i]
  }
  return result
}
console.log(sumUp(100,10,20)) // 130
```

14. The Spread Operator

```javascript
// split array into a list of values
let numbers = [1,2,3,4]
console.log( Math.max(numbers) )    // NaN
console.log( Math.max(...numbers) ) // 4
```

15. The for-of loop

```javascript
// quickly access individual element in the array
let nums = [1.23, 1.10, 4.1]
for( let num of nums ) {
  console.log(num)
}
```

16. Template Literals

```javascript
// backtick
let name = 'Max';
let description = `
  Hello,
  ${name  + ' !!!!'} // also support calculations in the {}, use \$ to escape the special syntax
`
```

17. Destructuring Array

```javascript
// quick way to copy the values from an array
let numbers = [1, 2, 3];

// case 1
let [a, b, c, d] = numbers;
console.log(a)       // 1
console.log(d)       // undefined
console.log(numbers) // [1, 2, 3]

// case 2
let [m, ...n] = numbers;
console.log(n) // [2, 3]

// case 3
let [a = 'Default', b, c, d = 'Default'] = numbers
console.log(a) // 1
console.log(d) // 'Default'

// case 4: swap values
let a = 5;
let b = 10;
[b, a] = [a, b];
console.log(b) // 5
console.log(a) // 10

// case 5
let [a, , c] = numbers
console.log(a) // 1
console.log(b) // 2

let [a, b] = [1, 2, 3]
console.log(a, b)
```

18. Destructing Object
