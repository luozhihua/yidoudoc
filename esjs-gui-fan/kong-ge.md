#空格

#### 1. `逗号` `===` `!==` `<` `>` `||` `&&` `+` `-` `*` `/`等操作符前后必须留一个空格

***错误***

```javascript
console.log(1,2,3,4)

if(variable===100){...}
if(variable!==80){...}
if(variable<80){...}
if(variable>80){...}
if(variable>80||age<18){...}
if(variable>80&&age<18){...}

let amount = product[0].price+product[1].price
let difference = product[0].price-product[1].price
```
***正确***

```javascript
console.log(1, 2, 3, 4)

if (variable === 100) {...}
if (variable !== 80) {...}
if (variable < 80) {...}
if (variable > 80) {...}
if (variable > 80 || age < 18) {...}
if (variable > 80 && age < 18) {...}

let amount = product[0].price + product[1].price
let difference = product[0].price - product[1].price
```

#### 2 `if` `else` `switch` `while` `do while`等关键字与小括号、大括号之间留一个空格

***错误***
```javascript
if(typeof window.console !== 'undefined'){
  console.log(1)
}else{
  alert(2)
}

switch(user.gender){
  case 'male':
    console.log('我是男人')
    break

  case 'female':
    console.log('我不是男人')
    break

  default:
    console.log('我也不知道自己是不是男人')
}

while(i<20){
  i = i+1
  console.log(i)
}

do{
  i = i+1
  console.log(i)
}while(i<10)
```

***正确***

```javascript
if (typeof window.console !== 'undefined') {
  console.log(1)
} else {
  alert(2)
}

switch (user.gender) {
  case 'male':
    console.log('我是男人')
    break

  case 'female':
    console.log('我不是男人')
    break

  default:
    console.log('我也不知道自己是不是男人')
}

while (i<20) {
  i = i + 1
  console.log(i)
}

do {
  i = i + 1
  console.log(i)
} while (i < 10)
```


#### 3. function、class的大括号之前必须留一个空格

***错误***
```javascript
function loadData(){
  this.$ajax.get('/api/xxx')
}

const loadData = function(){
  this.$ajax.get('/api/xxx')
}

class Analysis{
  constructor() {...}
}
```

***正确***

```javascript
function loadData() {
  this.$ajax.get('/api/xxx')
}

const loadData = function() {
  this.$ajax.get('/api/xxx')
}

class Analysis {
  constructor() {...}
}
```

#### 4. 函数和方法的参数之间必须留空格

***错误***

```javascript

function loadProducts(url,categoryId) {...}

class Student extend Person {
  constructor(studentNumber,foo,bar,baz) {
    ...
  }
}
```

***正确***

```javascript

function loadProducts(url, categoryId) {...}

class Student extend Person {
  constructor(studentNumber, foo, bar, baz) {
    ...
  }
}
```