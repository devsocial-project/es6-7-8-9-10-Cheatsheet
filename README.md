
# Es6, Es7, Es8 Cheat Sheet

A complete, simple, easy to use cheat sheet for ES6, ES7, ES8.
Support us at:
- Website: [http://devsocial.io/](http://devsocial.io/)
- YouTube: [Devsocial](https://www.youtube.com/channel/UCShL9oRNWYyfrqBuDi6uZpA)


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
	//-->1,2,3,4,5]
const arrayName = [9,8,7,6] 
	//-->SyntaxError
```
You can change, add value to a constant object  but you cannot reassign or redefine it:
```javascript
const person = {name:"DevSocial",email:"support@devsocial.io",city:"L.A"}
person.name ="OtherName" //change a property 
person.location = "U.S" //add a new property
person = {name:"Daniel",email:"daniel@devsocial.io",city:"L.A"} 
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
let variables cannot be redefined:
```javascript
let variableName = "other value"  
	//-->SyntaxError
```
### Hoisting - `var` vs `let`:

Variable defined by `var` get hoisted at the top
```javascript
console.log(sayHello)
	//-->undefined
//variable sayHello is hoisted at the top before it was defined
var sayHello = "HelloWorld" 
console.log(sayHello)
	//-->"HelloWorld"
```
Variable defined by `let` doesn't get hoisted at the top
```javascript
console.log(sayHello)
	 //-->ReferenceError
let sayHello = "HelloWorld"
console.log(sayHello)
	//-->"HelloWorld"

```
`let` should be used in `for` loop instead of `var`:
```javascript
//with var
for (var i = 0; i < 3; i++) {
 	console.log(i);
 	setTimeout(function(){
      	console.log("The number is " + i);
 	}, 1000);
};
//after 1 sec
     //-->The number is 5  (x3)   
//setTimeout reference i after when the for loop ends
console.log(i)
	//--> 3
//i is leaked outside the for loop
```
```javascript
//with let
for (let i = 0; i < 3; i++) {
 	setTimeout(function(){
      	console.log("The number is " + i);
 	}, 1000);
}
     //-->The number is 1
     //-->The number is 2
     //-->The number is 3
```

## Template Strings

You can reference variable, do math inside a template string:
```javascript
let first = "Dev";
let last = "Social";
let num1 = 2;
let num2 = 3;
console.log(`Hello ${fist}${last} ${num1+num2}`); 
     //-->  "Hello DevSocial 5"
 console.log(`Hello ${fist}
 ${last}`); 
	 //-->"Hello Dev
	//Social"
```
## Arrow function
> Arrow function is a new way of defining a function for cleaner code and is commonly used in callback function

Define an arrow function with `return`:
```javascript
let functionName = (para1,para2) => { 
     sum = para1+para2;
     return sum; 
}    
```
Define an arrow function without `return`:
```javascript
let functionName = (para1, para2) => (para1 +para2) ;  
//parentheses are optional, but advised 
let functionName = para1, para2 => para1 +para2 ;  
```
```javascript
//Same way in ES5
function (para1,para2){
     return para1+para2;
}
```
Arrow function is commonly used in callback:
```javascript
 let doubleThenFilter = arr => arr.map(value => (value *2) )
                                    .filter(value => (value % 3 === 0))
```
```javascript
//Same way in ES5
function doubleThenFilter(arr){
 	return arr.map(function(value){
      	return value *2;
 	}).filter(function(value){
      	return value % 3 === 0;
 	})
};
```
## Spread Operator
A spread operator would break down an array into values so that they can be easily used:
```javascript
let nums = [4,5,6,7,8]
let nums2 = [1,2,3,...nums,9,10]
console.log(nums2)
	//--> [1,2,3,4,5,6,7,8,9,10]
```
Spread operator is commonly used when a function doesn’t accept an array as a parameter:
```javascript
function sumValues(a,b,c){
 	console.log(arguments);  //print out the arguments of the function
return a+b+c;
}
let nums = [2,3,4]
sumValues(...nums) //values 2,3,4 of nums array has been passed to a,b,c parameters
	//-->[2,3,4]
	//-->9
sumValues(5,5,...nums) //value 2 of nums array has been passed to c parameter
	//-->[5,5,2,3,4]
	//-->12
```
```javascript
//Another example
let nums = [1,2,3,4]
Math.min(nums)
	//--> NaN
Math.min(...nums)
	//-->1
```
## Rest Operator
Rest operator is commonly used in a function when you don’t know the number of input arguments passed into the function:
```javascript
function printRest(a,b,...args){
	console.log(a);
	console.log(b);
	console.log(args); //args is the array of arguments
	console.log(...args); //...args are values that has been broken down
}
printRest(1,2,3,4,5)
	//-->1
	//-->2
	//-->[3,4,5]
	//-->3 4 5
```
```javascript
function smallest(...args){
     return "Smallest number is " + Math.min(...args);
}
smallest(1,2,3,4,5)
	//--> "Smallest number is 1"
```
## Default Parameter
Set default value to the parameter:
```javascript
//without default parameter
function sum(nums) {
	let total = 0;
	nums.forEach((d)=>(total+=d));
	return total
}
sum();
	//-->TypeError

//with default parameter
function sum(nums =[]) {
	let total = 0;
	nums.forEach((d)=>(total+=d));
	return total
}
sum();
	//-->0
```
## Array Destructuring
Assign values from an array to different variables:
```javascript
var arr = [1,2,3]
var [a,b,c] = arr;
console.log(a) //-->1
console.log(b) //-->2
console.log(c) //-->3
```
## Object Destructuring
### Unpack an object:
Variable with the same names as properties:
```javascript
var person = {
     first: “Dev”;
     last: “Social”;
}
//define and assign value to variables with the same name as properties in the object
var { fist, last } = person;
console.log(fitst)
	//-->"Dev"
console.log(last)
	//-->"Social"

```
Variables with different names from properties:
```javascript
var person = {
     first: “Dev”;
     last: “Social”;
}
//define and assign values to variables with different names from properties in the object
var { newFirst:first, newLast:last } = person;    
console.log(newFirst) 
	//-->"Dev"
console.log(newLast) 
	//-->"Social"

```
### Object Destructuring Default Parameters:

```javascript
function createPerson( { 
	name = {
		first:"Dev",
		last: "Social",
		}, isFun = false ,
	} = {} ) {
		return [name.first, name.last, isGood);
createPerson() 
	//-->["Dev", "Social", false]
createPerson( { isFun:true } ) 
	//-->["Dev", "Social", true]
createPerson( { name: { first: "Daniel", last:"N"} }); 
	//--> ["Daniel", “N”, false]

```
## Class
> Class in ES6 or above is a combination of constructor functions and prototypes in ES5 that make Object Oriented Programing in Javascript more clean and readable

`class` will define a constant and `class` does not hoist.

### Class Object

Define a `class` object. this `class` will replace constructor function and prototypes in ES5:
```javascript
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
newPerson.multiplyFavoriteNum(10) 
	//-->70
```
```javascript
//Same way in ES5
function Person(firstName, lastName, favoriteNum) { //this is a constructor function
	this.firstName = firstName;
	this.lastName = lastName;
	this.favoriteNum = favoriteNum;
}
Person.prototype.multiplyFavoriteNum = function(num){
	return num*this.favoriteNum
}
var newPerson = new Person("Dev","Social",7);
newPerson.multiplyFavoriteNum(10) 
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
}

var newPerson = new Person("Dev","Social","blue",7)
newPerson.callStatic()
	//-->ERROR
Person.callStatic() 
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
}

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
## Import/Export

**Named export:** You can export an object or objects in a .js file and then import that object to another .js file:

*file1.js*
```javascript
export sayHello = "HelloWorld"
export sayHi ="Hi"
```
*file2.js*
```javascript
import { sayHello, sayHi } from "./file1.js"
console.log(sayHello)
	//-->"Hello"
console.log(sayHi)
	//-->"Hi"
```
**Default export:** You can only export one default object in a .js file and then import that object in another .js file. However, you don't need curly brackets when importing:

*file1.js*
```javascript
export default sayHello = "HelloWorld"
```
*file2.js*
```javascript
import { sayHello, sayHi } from "./file1.js"
console.log(sayHello)
	//-->"Hello"
```
**Exporting a Class:** Export/import are commonly use to export/import classes:

*vehicle.js*
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
*car.js*
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
