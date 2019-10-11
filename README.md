**Es6, Es7, Es8 Cheat Sheet******

------------


A complete, simple, easy to use cheat sheet for ES6, ES7, ES8.
Support us at:
- Website: devsocial.io
- YouTube: [Devsocial](https://www.youtube.com/channel/UCShL9oRNWYyfrqBuDi6uZpA)

**Table of Contents**

[TOC]

## Define variables (const & let)
### const 
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
### let 
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
**Hoisting - `var` vs `let`:**

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
`let `should be used in `for` loop instead of `var`:
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
##Template Strings
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
##Arrow function
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
//Same way without ES6
function (para1,para2){
     return para1+para2;
}
```
Arrow function is commonly used in callback:
```javascript
 let doubleThenFilter = arr => arr.map(value => (value *2) )
                                    .filter(value => (value % 3 === 0))
```
