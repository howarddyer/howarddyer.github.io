---
layout: post
title:  "JavaScript ES5 Array Methods Recap"
date:   2018-10-20 17:00:00
label:  note
---

## forEach
*Array.prototype.forEach(function callback(item, [index, array]))*

This method:
* executes the callback function on all items in the Array
* returns undefined

```javascript
var employees = [
    { name: "Jack", age: 36 },
    { name: "Jill", age: 35 },
    { name: "James", age: 41 }
]

employees.forEach(function(employee) {
    console.log(employee.name);
})

//  Jack
//  Jill
//  James
```

## map
*Array.prototype.map(function callback(item, [index, array]))*

This method:
* executes the callback function on all items in the Array
* returns a new array of the same size as the original

```javascript
var employees = [
    { name: "Jack", age: 36 },
    { name: "Jill", age: 35 },
    { name: "James", age: 41 }
]
var employeesIn30Years = employees.map(function(employee) {
    return {
        name: employee.name,
        ageIn30Years: employee.age + 30
    }
})

console.log(employeesIn30Years)

//  [
//      { name: "Jack", ageIn30Years: 66 },
//      { name: "Jill", ageIn30Years: 65 },
//      { name: "James", ageIn30Years: 71 }
//  ]
```

## filter
*Array.prototype.filter(function callback(item, [index, array]))*

This method:
* executes the callback function on all items in the Array
* returns a new array of items that pass the callback function

```javascript
var employees = [
    { name: "Jack", age: 36 },
    { name: "Jill", age: 35 },
    { name: "James", age: 41 }
]
var employeesOver35 = employees.filter(function(employee) {
    return employee.age > 35
})

console.log(employeesOver35)

//  [
//      { name: "Jack", age: 36 }
//      { name: "James", age: 41 }
//  ]
```

## every
*Array.prototype.every(function callback(item, [index, array]))*

This method:
* executes the callback function on each item in the Array
* returns true if every item passes the callback function
* returns false if at least one item does not pass the callback function

```html
<form class="js-new-employee-form">
    <input type="text" name="name">
    <input type="number" name="age">
    <button type="button">
</form>
```

```javascript
var inputNodes = document.querySelectorAll(".js-new-employee-form input")
var submitButtonNode = document.querySelector(".js-new-employee-form button")

submitButtonNode.addEventListener("click", function() {
    var inputsArray = Array.from(inputs);
    var allInputsHaveValues = inputNodes.every(function(inputNode) {
        return inputNode.value !== ""
    })

    if (!allInputsHaveValues) {
        console.log("Error: All form fields are required");
        return;
    }
})
```

## some
*Array.prototype.some(function callback(item, [index, array]))*

This method:
* executes the callback function on each item in the Array
* returns true if at least one item passes the callback function
* returns false if none of the items pass the callback function

```javascript
var employees = [
    { name: "Jack", age: 36 },
    { name: "Jill", age: 35 },
    { name: "James", age: 41 }
]
var someEmployeesOlderThan40 = employees.some(function(employee) {
    return employee.age > 40
})
var someEmployeesOlderThan50 = employees.some(function(employee) {
    return employee.age > 50
})

console.log(someEmployeesOlderThan40, someEmployeesOlderThan50)

//  true false
```

## reduce
*Array.prototype.reduce(function callback(accumulator, currentValue, [index, array]), originalValue)*

This method:
* executes the callback function on every item in the Array, using an accumulator
* returns a single value
* accepts an originalValue that is the same type as the returned value
* If nothing is given for originalValue, the first item in the array is used

```html
<p class="js-introduction-text"></p>
<ul class="js-employee-images-list"></ul>
```

```javascript
var employees = [
    { name: "Jack", age: 36, imageUrl: "http://fakecompany.com/images/jack.png"  },
    { name: "Jill", age: 35, imageUrl: "http://fakecompany.com/images/jill.png"  },
    { name: "James", age: 41, imageUrl: "http://fakecompany.com/images/james.png"  }
]
var nodeIntroText = document.querySelector("js-introduction-text");
var nodeEmployeeImagesList = document.querySelector("js-employee-images-list");

var ageOfCompany = employees.reduce(function(total, employee) {
    return total + employee.age
}, 0)

nodeIntroText.innerHTML = `Our company has ${ageOfCompany} years' experience.`
nodeEmployeeImagesList.innerHMTL = employees.reduce(function(list, employee) {
    return `${list}<li><img src="${employee.imageUrl}"</li>`
}, "")
```

## reduceRight
*Array.prototype.reduceRight(function callback(accumulator, currentValue, [index, array]), originalValue)*

This method:
* executes the callback function on every item in the Array, from right to left, using an accumulator
* returns a single value
* accepts an originalValue that is the same type as the returned value
* If nothing is given for originalValue, the first item in the array is used

```javascript
var employees = [
    { name: "Jack", age: 36, imageUrl: "http://fakecompany.com/images/jack.png"  },
    { name: "Jill", age: 35, imageUrl: "http://fakecompany.com/images/jill.png"  },
    { name: "James", age: 41, imageUrl: "http://fakecompany.com/images/james.png"  }
]

var employeeNames = employees.reduceRight(function(list, employee) {
    return `${list}${employee.name}, `
}, "")

console.log(employeeNames)

//  James, Jill, Jack
```
