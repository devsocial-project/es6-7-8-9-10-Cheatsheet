
# ES6, ES7, ES8, ES9, ES10 Cheat Sheet

A complete, simple, easy to use cheat sheet for ES6, ES7, ES8, ES9, ES10.

Support us at:
- Website: [http://devsocial.io/](http://devsocial.io/)
- YouTube: [Devsocial](https://www.youtube.com/channel/UCShL9oRNWYyfrqBuDi6uZpA)

## Table of Contents

 - [Define variables (const & let)](#define-variables-const--let)
 - [Template Strings](#template-strings)
 - [String.padStart() / String.padEnd()](#stringpadstart--stringpadend)
 - [Arrow function](#arrow-function)
 - [Spread Operator](#spread-operator)
 - [Rest Operator](#rest-operator)
 - [Default Parameter](#default-parameter)
 - [Array Destructuring](#array-destructuring)
 - [New Useful Array Methods(.from(), .include(), .flat(), . flatMap()](#new-useful-array-methods)
 - [Object Destructuring](#object-destructuring)
 - [New Useful Object Methods(.assign(), .entries(), fromEntries()](#new-useful-object-methods)
 - [Object Enhancements - Better way to handle an object](#object-enhancements)
 -  [For ... of Loop](#for-...-of-loop)
 - [Class](#class)
 - [Import/Export](#importexport)
 - [Hash map](#hash-map)
 - [Sets](#sets)
 - [Generator](#generator)
 - [Promise](#promise)
 - [Async/await](#asyncawait)
 - [Handling Errors (try/catch/throw/finally)](#handling-errors-trycatchthrowfinally)

## Define variables (const & let)
### `const`:
Define a constant variable:
```javascript
const variableName = "value"
```
Constant variables can not be changed or reassign or redefine:
```javascript
const variableName = "other value"  
    //-->SyntaxError
variableName = "other value" 
    //-->SyntaxError
```
You can change, add value to a constant array  but you cannot reassign or redefine it:
```javascript
const arrayName = [1,2,3,4]
arrayName.push(5) 
    //-->[1,2,3,4,5]
const arrayName = [9,8,7,6] 
    //-->SyntaxError
```
You can change, add value to a constant object  but you cannot reassign or redefine it:
```javascript
const person = {name:"DevSocial",email:"support@devsocial.io",city:"L.A"}
person.name ="OtherName" //change a property 
person.location = "U.S" //add a new property
person = {name:"Daniel",email:"daniel@devsocial.io",city:"L.A"} //reassign it 
    //-->SyntaxError
```
Constant variables exist in a block scope:
```javascript
var x = 1
{ //this is a block scope
    const x = 2
}
console.log(x) 
    //-->1
```
### `let`:
Define a let variable:
```javascript
let variableName = "value"
```
let variables exist in a block scope:
```javascript
var x = 1
{ //this is a block scope
    let x = 2
}
console.log(x) //-->1
```
let variables cannot be redefined, but can be reassigned:
```javascript
let variableName = "other value"  
    //-->SyntaxError
variableName = "other value"
```
### Hoisting - `var` vs `let`:

Variable defined by `var` get hoisted at the top
```javascript
console.log(sayHello)
    //-->undefined
//variable sayHello is hoisted at the top before it was defined by var
//This means that variable is there but with value of undefined
var sayHello = "HelloWorld" 
console.log(sayHello)
    //-->"HelloWorld"
```
Variable defined by `let` doesn't get hoisted at the top
```javascript
console.log(sayHello)
     //-->ReferenceError:sayHello is not defined
let sayHello = "HelloWorld"
console.log(sayHello)
    //-->"HelloWorld"

```
`let` should be used in `for` loop instead of `var` because variables defined by `var` will be leaked outside the `for` loop and will only reference the ending result of `i` if there is a `setTimeout` function:
```javascript
//with var
for (var i = 0; i < 3; i++) {
     console.log(i);
     setTimeout(function(){
          console.log("The number is " + i);
     }, 1000);
};
//after 1 sec
    //-->The number is 2  (x3)   
//setTimeout reference i after when the for loop ends
console.log(i)
    //--> 2
//i is leaked outside the for loop
```
```javascript
//with let
for (let i = 0; i < 3; i++) {
     setTimeout(function(){
          console.log("The number is " + i);
     }, 1000);
}
//after 1 sec
    //-->The number is 0
    //-->The number is 1
    //-->The number is 2
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Template Strings
Template string is a quick way for you to handle a string.

You can reference variables:
```javascript
let first = "Dev";
let last = "Social";

console.log(`Hello ${first}${last}`); 
     //-->  "Hello DevSocial"
```
You can use expression (i.e adding numbers):
```javascript
//More practical example
let num1 = 2;
let num2 = 3;
console.log(`The number is ${num1+num2}`); 
     //-->  "The number is 5"
```
You can just break a line, use tab without using `\n` `\t `:
```javascript
console.log(`Hello
World`)
    //-->"Hello
    //World"
```
```javascript
//More practical example

let channel_name = "desocial";
let base_url = "https://www.youtube.com/"
let url = `${base_url}channel/${channel_name}/`
    //-->"https://www.youtube.com/channel/desocial"
```   
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## String.padStart() / String.padEnd()

> .padStart(), .padEnd() are used to fill up a string to a certain number of characters

 **`.padStart()`**
 
.padStart() will add a certain number of characters at the beginning of a string to fill up the required string length.
```javascript
let maxlength = 15;
let string = "DevSocial"
console.log(string.padStart(maxlength,"a"))
    //-->"aaaaaaDevSocial"
```
**`.padEnd()`**

.padEnd() will add a certain number of character at the end of a string to fill up the required string length.
```javascript
let maxlength = 15;
let string = "DevSocial"
console.log(string.padEnd(maxlength,"a"))
    //-->"DevSocialaaaaaa"
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Arrow function
> Arrow function is a new way of defining a function for cleaner code and is commonly used in callback function

Define an arrow function with `return`:
```javascript
let functionName = (param1,param2) => { 
     sum = param1+param2;
     return sum; 
}    
```
Define an arrow function without `return`:
```javascript
let functionName = (param1, param2) => (param1 + param2) ;  
```
If there is no parameter, you can just use parentheses:
```javascript
let functionName = () => ("Hello world");  
```
```javascript
//Same way before ES6
function functionName(param1,param2){
     return param1+param2;
}
```
Arrow function is commonly used in callback:
```javascript
let myArr = [1,2,3]
let doubleThenFilter = arr => arr.map((value) => (value * 2) )
                                  .filter((value) => (value % 3 === 0));
doubleThenFilter(myArr)
```
```javascript
//Same way before ES6
function doubleThenFilter(arr){
    return arr.map(function(value){
        return value *2;
    }).filter(function(value){
        return value % 3 === 0;
    })
};
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Spread Operator
A spread operator would break down an array into values so that they can be easily used:
```javascript
let nums = [4,5,6];
let nums2 = [1,2,3,...nums,7,8];
console.log(nums2);
    //--> [1,2,3,4,5,6,7,8]
```
Spread operator is commonly used when a function doesn’t accept an array as a parameter:
```javascript
function sumValues(a,b,c){
     console.log(arguments);  //print out an array of the arguments of the function
return a+b+c;
}
let nums = [2,3,4];
sumValues(...nums); //values 2,3,4 of nums array has been passed to a,b,c parameters
    //-->[2,3,4]
    //-->9
sumValues(5,5,...nums); //value 2 of nums array has been passed to c parameter
    //-->[5,5,2,3,4]
    //-->12
```
```javascript
//Another example
let nums = [1,2,3,4];
Math.min(nums);
    //--> NaN
Math.min(...nums);
    //-->1
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Rest Operator
Rest operator is commonly used in a function when you don’t know the number of input arguments passed into the function:
```javascript
function printRest(a,b,...args){
    console.log(a);
    console.log(b);
    console.log(args); //args is the array of arguments
    console.log(...args); //...args are values that has been broken down
}
//args is just a name, you can name it with anything
printRest(1,2,3,4,5);
    //-->1
    //-->2
    //-->[3,4,5]
    //-->3 4 5
```
```javascript
function smallest(...args){
     return "Smallest number is " + Math.min(...args);
}
smallest(1,2,3,4,5);
    //--> "Smallest number is 1"
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Default Parameter
Set default value to the parameter:
```javascript
//without default parameter
function sum(nums) {
    let total = 0;
    nums.forEach((d)=>(total+=d));
    return total;
};
sum();
    //-->TypeError

//with default parameter
function sum(nums =[]) {
    let total = 0;
    nums.forEach((d)=>(total+=d));
    return total;
};
sum();
    //-->0
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Array Destructuring
Assign values from an array to different variables:
```javascript
var arr = [1,2,3];
var [a,b,c] = arr;
console.log(a); //-->1
console.log(b); //-->2
console.log(c); //-->3
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## New Useful Array Methods
The new array methods that would come in handy in ES6,7,8,9.

**`Array.from`** *(Not yet supported by Edge)*

Convert array-like-object into an array.  An array-like-object is an object but looks like an array.
```javascript
let myDivs = document.querySelector("div"); //This will return an array-like-object
let mySet = new Set([1,1,2,2,3,3]); //Set is also an array-like object
let arrConvert = Array.from(mySet);
    //--> [1,2,3]
```

**`.includes()`**

Check if an item exist in an array, return Boolean:
```javascript
let myArr = [1,2,3,4,5];
console.log(myArr.includes(2));
    //-->true
```
**`.flat()`** *(Not yet supported by Edge)*

Flatten a nested array, remove empty spots; then return a new array:
```javascript
let myArr = [1,2,,[3,4]];
myArr.flat();
    //-->[1,2,3,4]
let myArr2 = [1,2,[3,4,[5,6]]];
myArr2.flat();
    //-->[1,2,3,4,[5,6]];
```
You can assign the depth level of `.flat()`:
```javascript
let myArr2 = [1,2,[3,4,[5,6]]];
myArr2.flat(2);
    //-->[1,2,3,4,5,6];
myArr2.flat(Infinity); //Infinity would flatten until there's no nested array
    //-->[1,2,3,4,5,6]
```
**`.flatMap()`** *(Not yet supported by Edge)*

An upgrade version of `.map()` in the case that `.map()` return a nested array, `.flatMap()` would flatten it:
```javascript
let myArr = [1, 2, 3, 4];

myArr.map(x => [x * 2]); 
// [[2], [4], [6], [8]]

myArr.flatMap(x => [x * 2]);
// [2, 4, 6, 8]
```
```javascript
//A more practicle example
let myArr= ["Javascript is fun", "and", "ES2019 is also fun"];

myArr.map(x => x.split(" "));
// [["Javascript","is","fun"],["and"],["ES2019", "is", "also", "fun"]]

myArr.flatMap(x => x.split(" "));
// ["Javascript", "is", "fun", "and", "ES2019", "is", "also", "fun"]
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Object Destructuring
### Unpack an object:
Define and assign value to variables with the same names as properties:
```javascript
const person = {
     first:"Dev",
     last: "Social",
}
//define and assign value to variables with the same name as properties in the object
let { first, last } = person;
console.log(first)
    //-->"Dev"
console.log(last)
    //-->"Social"

```
Define and assign value to variables with different names from properties:
```javascript
const person = {
     first:"Dev",
     last: "Social",
}
//define and assign values to variables with different names from properties in the object
let { first:differentFirst, last:differentLast} = person;    
console.log(differentFirst) 
    //-->"Dev"
console.log(differentLast) 
    //-->"Social"

```
Define and assign value to variables and exclude unwanted variables using spread operator:
```javascript
const person = {
    first:"Dev",
    last:"Social",
    city:"L.A",
    state:"CA",
    country:"USA",
};
const { state, ...personWithoutState } = person;
console.log(state);
    //-->"CA"
console.log(personWithoutState);
    //-->{first: "Dev", last: "Social", city: "L.A", country: "USA"}
```
### Object Destructuring Default Parameters:
You can assign default parameter value as a destructured object 
```javascript
function createPerson({ 
    name = {
        first:"Javascript",
        last: "ES6",
        }, 
    isFun = false,
    } = {}){ //an empty object need to be assigned to the destructured object
    return [name.first, name.last, isFun];
}
createPerson();
    //-->["Javascript", "ES6", false]
createPerson({ isFun:true });
    //-->["Javascript", "ES6", true]
createPerson({name:{ first: "Dev", last:"Social"}}); 
    //--> ["Dev", “Social”, false]
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## New Useful Object Methods
The new object methods that would come in handy in ES6,7,8,9.

**`Object.assign()`**

`Object.assign()` is commonly used to properly clone an object, since you just cannot simply clone an obj by assign the object equal to another object.
```javascript
//NOT A WAY OF CLONING AN OBJECT
let obj1 = {name:"DevSocial"};
let obj2 = obj1; // this will not clone obj1, but only assign a reference to obj1
obj2.name = "some text";
console.log(obj1.name);
    //-->"some text"
```
```javascript
//BETTER WAY OF CLONING AN OBJECT
let obj1 =  {name:"DevSocial"}; 
let obj2 = Object.assign({},obj1);
obj2.name = "some text";
console.log(obj1.name);
    //-->"DevSocial"
```
`Object.assign()` however is not a deep clone. If the object's property holds a value of an array, that array still have a reference in the cloned object:
```javascript
//NOT A DEEP CLONE
let obj1 =  {myArr:[1,2,3]}; 
let obj2 = Object.assign({},obj1);
obj2.myArr.push(4)
console.log(obj1.myArr);
    //-->[1,2,3,4]
```
**`.entries() / .fromEntries()`**

`.entries()` would convert the key:value pairs of an object into an array that holds [key,value] pairs.
```javascript
const myObj = {
    key1: "value1",
    key2: "value2",
    key3: "value3",
};
const entries = Object.entries(myObj);
console.log(entries);
    //--> [["key1","value1"],["key2","value2"],["key3","value3"]]
```
`.fromEntries()` would convert [key,value] pairs of an array into key:value pairs of an object :
```javascript
const myObj2 = Object.fromEntries(entries);
console.log(myObj2);
    //--> {key1:"value1", key2:"value2", key3:"value3"}
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Object Enhancements
###  Object property as a variable
You can set a property of an object with the value of a variable:
```javascript
let somevar = "firstName";  
let person = {  
[somevar]: "Dev"
};
console.log(person);
    //-->{firstname:"Dev"}
```
### Shorten Object methods
You can shorten the object methods inside an object:
```javascript
//ES6 and above
let myObj ={
    sayHello(){
        console.log("Hello World");
    }
}

//Before ES6
var myObj ={
    sayHello: function(){
    console.log("Hello World");
    }
}
```
[↑ Back to top](#es6-es7-es8-es9-cheat-sheet)

## For ... of Loop
A `for` `of` loop introduce a simpler way to iterate the values of  a iterable object (a string, an array, a set, a map, a generator, or a DOM collection). 
```javascript
let myArr =[1,2,3];
for (let num of myArr){
    console.log(num)
}
    //-->1
    //-->2
    //-->3

let myStr = "Hello"
for (let ch of myStr){
    console.log(ch)
}
```

`for` `of` is only designed for iterating the value of an iterable object, not for updating it:
```javascript
let myArr =[1,2,3];
for (let num of myArr){
    num +=1;
};
console.log(myArr);
    //-->[1,2,3]
// myArr was not updated
// If you want to update it, you need to use a temporary object to store the value
let tempArr = [];
for (let num of myArr){
    num +=1;
    tempArr.push(num);
};
myArr = tempArr;
console.log(myArr);
    //-->[2,3,4]
```
More about iteration with other iterable objects can be found at: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of)

[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Class
> Class in ES6 or above is a combination of constructor functions and prototypes in ES5 that make Object Oriented Programing in Javascript more clean and readable

`class` will define a constant and `class` does not hoist.

### Class fundamentals
Define a `class` object. this `class` will replace constructor function and prototypes in ES5:
```javascript
//ES6 and above
class Person {
     constructor(firstName, lastName, favoriteNum){
          this.firstName = firstName;
          this.lastName = lastName;
          this.favoriteNum = favoriteNum;
     }
     multiplyFavoriteNum(num){  
          return num * this.favoriteNum;
     }
};
let newPerson = new Person("Dev","Social",7);
newPerson.multiplyFavoriteNum(10) ;
    //-->70
```
```javascript
//Same way before ES6
function Person(firstName, lastName, favoriteNum) { //this is a constructor function
    this.firstName = firstName;
    this.lastName = lastName;
    this.favoriteNum = favoriteNum;
}
Person.prototype.multiplyFavoriteNum = function(num){
    return num*this.favoriteNum;
}
var newPerson = new Person("Dev","Social",7);
newPerson.multiplyFavoriteNum(10) ;
    //-->70
```
### Static

`Static` is a function that only accessed by the `class` object. Other objects that are created from class object cannot access `static`:
```javascript
class Person {
     constructor(firstName,lastName,favoriteNumber){
          this.firstName = firstName;
          this.lastName = lastName;
          this.favoriteNum = favoriteNum;
     }
     multiplyFavoriteNum(num){   
          return num * this.favoriteNum;
     }
     static callStatic(){
          return "static has been called"
     }
};

var newPerson = new Person("Dev","Social","blue",7);
newPerson.callStatic();
    //-->ERROR
Person.callStatic() ;
    //-->"static has bene called"

```
### Inheritance
A class can inherit anotther class using `extends` key word and `super` keyword:

```javascript
class Vehicle{
    constructor(make,model,year){
        this.make=make;
        this.model=model;
        this.year=year;
    }
    start(){
        return `${this.make} ${this.model} ENGINE START`;
    }
};

class Car extends Vehicle{
    constructor(make,model,year,numWheels){
        super(make,model,year);   //inherit make,model,year from Vehicle
        this.numWheels = 4;
    }
};
var newCar = new Car("Honda","Civic",2019);
newCar.numWheels;
    //-->4
newCar.start();
    //-->"Honda Civic ENGINE START"
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Import/Export

**Named export:** You can export an object or objects in a .js file and then import that object to another .js file:

*file1.js:*
```javascript
export sayHello = "HelloWorld";
export sayHi ="Hi";
```
*file2.js:*
```javascript
import { sayHello, sayHi } from "./file1.js";
console.log(sayHello);
    //-->"Hello"
console.log(sayHi);
    //-->"Hi"
```
You can rename the named imports
```javascript
import { sayHello as Hello, sayHi as Hi } from "./file1.js"
console.log(Hello);
    //-->"Hello"
```
You can import everything using `*`
```javascript
import * from "./file1.js";
console.log(sayHello);
    //-->"Hello"
```
**Default export:** You can only export one default object in a `.js` file and then import that object in another `.js` file. However, you don't need curly brackets when importing:

*file1.js:*
```javascript
export default sayHello = "HelloWorld";
```
*file2.js:*
```javascript
import sayHello from "./file1.js";
console.log(sayHello);
    //-->"Hello"
```
**Exporting a Class:** Export/import are commonly use to export/import classes:

*vehicle.js:*
```javascript
class Vehicle{
    constructor(make,model,year){
        this.make=make;
        this.model=model;
        this.year=year;
    }
    start(){
        return `${this.make} ${this.model} ENGINE START`;
    }
}
export default Vehicle;
```
*car.js:*
```javascript
import Vehicle from "./vehicle.js"

class Car extends Vehicle{
    constructor(make,model,year,numWheels){
        super(make,model,year);   //inherit make,model,year from Vehicle
        this.numWheels = 4;
    }
}
var newCar = new Car("Honda","Civic",2019)
newCar.numWheels
    //-->4
newCar.start()
    //-->"Honda Civic ENGINE START"
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Hash map

> Hash map is an object that contains key-value pairs. Any value (including array, object, Boolean, number, function)  can be used as a key or a value. A Hash map stores the insertion orders.

Define a new Hash Map:
```javascript
let myMap = new Map;
```
Insert or set a key-value pair:
```javascript
myMap.set(1,"something");
myMap.set(false,"something");
myMap.set([1,2,3],"something");
myMap.set({1:"abc"},"something");
```
Delete a key-value pair:
```javascript
myMap.delete(false);
```
Check if a key exist:
```javascript
myMap.has(1);
```
Check a map size:
```javascript
myMap.size;
```
Get  a value:
```javascript
myMap.get(1);
```
Remove all key-value pairs:
```javascript
myMap.clear();
```
`.keys()` would return a map iterator of keys

`.values()` would return a map iterator

You can iterate a map iterator using  `for` `of`:
```javascript
for (let [key, value] of myMap) {
  console.log(key + ' = ' + value);
};
for (let key of myMap.keys()) {
  console.log(key);
};
for (let value of myMap.values()) {
  console.log(value);
};
```
More about hash map can be found at: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Sets

> A set is a collection of unique values. A set is not an ordered abstract data structure, which means you cannot sort a set or order doesn't matter.

Define a set:
```javascript
const mySet = new  Set([3,1,1,2,2,4]);
//--> {3,1,2,4}
```
Add a new value:
```javascript
mySet.add(5);
//-->{3,1,2,4,5}
```
Check if a value exist:
```javascript
mySet.has(3);
//-> true
```
Check a set’s size:
```javascript
mySet.size;
//->5
```
Delete a value in a set:
```javascript
mySet.delete(3);
//-->true
```
More about sets can be found at: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set)

[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Generator

> A Generator is like a function, however, it can be paused and continue

Define a generator, `yield` in a generator is almost the same to `return`  :
```javascript
function* genValues(){
    yield "first";
    yield "second";
    yield "third";
};
let myGen = genValues()
```
Run a generator:
```javascript
myGen.next() //.next() run the gen and return an object
    //--> {value:"first", done:false}
myGen.next().value    //.value returns the next gen value
    //--> "second"
myGen.next().done //.done returns the status of the gen
    //--> false
myGen.next()
    //-->{value:undefined, done:true}
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Promise

> The **`Promise`** object represents the eventual completion (or failure) of an asynchronous call, and its resulting value.

Promise is one of the fundamental concepts in Asynchronous JavaScript, Ajax, React,... 
Asynchronous JavaScript is simply when your code is not sequentially executed at a time. For example, `setTimeout`, `setInterval`, ajax calls,... that take a period of time to be fulfilled.
```javascript
console.log("you want this executed first");
setTimeout(()=>{console.log("you want this executed second")},1000);
console.log("you want this executed third");
    //-->"you want this executed first"
    //-->"you want this executed third"
//after 1 sec
    //-->"you want this executed second"
```
With the example above, your code doesn't wait for `setTimeout`,  however,  you want your code to wait for that `setTimeout` before continuing, that's why you need `Promise`
### Promise fundamentals
A `Promise` has 4 main keywords: `resolve`, `then`, `reject`,`catch`:
 - `resovle` means that the promise has been fulfilled, and `then` is executed. `resovle` is almost the same to the way `return` works
 - `reject` means that the promise has not been fulfilled, and `catch` is executed. `reject` is almost the same to the way `return` works

```javascript
const promiseDoHomework = new Promise(function(resolve,reject) {
    let isDone = false;
    if (isDone){
        setTimeout(function(){
            resolve("is done");
        },1000)
    }else{
        setTimeout(function(){
            reject("is not done");
        },1000)
    }
});
promiseDoHomework.then(function(homeworkResult){
    console.log("The homework " + homeworkResult);
}).catch(function(homeworkResult){
    console.log("The homework " + homeworkResult);
})
    //-->"The homework is not done"
```

### Promise Chain
A chain of tasks can be sequentially executed. 
```javascript
const doHomework = function(){  
    return new Promise(function(resolve,reject){
        setTimeout(function(){
            resolve("Do Homework, ");
            console.log("Finished homework")
        },1000);
    })  
};  
const haveDinner = function(message){  
    return new Promise(function(resolve,reject){ 
         setTimeout(function(){
            resolve(message +"then "+ "have dinner, "); 
            console.log("Finished dinner")
        },1000);

    })  
};  
const takeShower= function(message){  
    return new Promise(function(resolve,reject){  
        setTimeout(function(){
            resolve(message + "then " + "take shower, "); 
            console.log("Finished shower")
        },1000);
    })  
};  
  
//call doHomework -> haveDinner -> takeShower
doHomework().then(function(message){  
    return haveDinner(message);  
}).then(function(message){  
    return takeShower(message);  
}).then(function(message){  
    console.log(message,"all finished ")  
})  
    //-->Finished homework
    //-->Finished dinner
    //-->Finished shower
    //-->Do Homework, then have dinner, then take shower,  all finished 
```
Call multiple tasks at the same time, only trigger `then` or `catch` when all of the tasks have been fulfilled/rejected:
```javascript
Promise.all([doHomework(),haveDinner(),takeShower()])
    .then(function(){
            console.log("all finished");
        });
```
Call multiple tasks at the same time, trigger `then` or `catch` when one of the tasks has been fulfilled/rejected:
```javascript
Promise.race([doHomework(),haveDinner(),takeShower()])
    .then(function(){
            console.log("one finished");
        });
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Async/await
### Async
The `ansync` keyword that placed before a function makes sure that the function always return a promise:
```javascript
async function myFunc(){
    return "this is a promise";
}
myFunc().then((val)=>{console.log(val)});
    //-->"this is a promise"
```
### Await
The `await` keyword is only used in the `async` function. The `await` keyword makes your code wait until the `Promise` inside the function has been fulfilled/rejected:
```javascript
async function myFunc(){
    let myPromise = new Promise((resolve,reject)=>{
        setTimeout(()=>{resolve("done!")},1000)
    });
    let result = myPromise.then((val)=>(val));
    return result;
}
myFunc().then((result)=>{console.log(result)})

```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)
## Handling Errors (try/catch/throw/finally)
`try` would test the block of code for errors. The code will run normally until there's an error.

`catch` would execute in case of there's an error in `try`.

`throw` allows you to custom your own error

`finnaly` would execute regardless of `try`  `catch`

```javascript
try{
    UndefinedFunction(); //this function was not defined
}catch(err){
    console.log("The error is " + err);
}
    //-->"The error is ReferenceError"
```
```javascript
try{
    let age = 16;
    if(age >= 18){
        console.log("You can view the content")
    }else{
        throw "You are not 18 to view the content";
    };
}catch(err){
    console.log(err)
}finally{
    console.log("Here's the content, you gonna fake your age anyway")
}
    //--> "You are not 18 to view the content"
    //--> "Here's the content, you gonna fake your age anyway"
```
[↑ Back to top](#es6-es7-es8-es9-es10-cheat-sheet)

## License
**Released under MIT License**

Copyright (c) 2019 DevSocial.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
