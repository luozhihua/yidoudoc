#条件与判断

#### 禁止使用`==` 和 `!=`

***错误***

```javascript
let foo = '1'
if (foo == 1) {
    ...
}

let bar = 0
if (bar == false) {
    console.log('bar is false')
} else {
    console.log('bar is true')
}

let bat = []
if (bat == false) {
    console.log('bat is false')
} else {
    console.log('bat is not false')
}

let baz = ''
if (baz == false) {
    console.log('baz is false')
} else {
    console.log('baz is not false')
}
```


***正确***

```javascript
let foo = '1.5'
if (Number(foo) === 1.5) {
    ...
}

let bar = 0
if (bar === false) {
    console.log('bar is false')
} else {
    console.log('bar is true')
}

let bat = []
if (bat === false) {
    console.log('bat is false')
} else {
    console.log('bat is not false')
}

let baz = ''
if (baz === false) {
    console.log('baz is false')
} else {
    console.log('baz is not false')
}
```

#### 不能省略 if后面的`{` 和 `}`
***错误***

```javascript
    if (foo) bar()
    
    if (baz) bat()
    else bar()
```

***正确***

```javascript
if (foo) {
    bar()
}

if (baz) {
    bat()
} else {
    bar()
}
```

#### 禁止用三元表达式执行函数

***错误***

```javascript
user.active ? foo() : bar()
```

***正确***

```javascript
if (user.active) {
    foo()
} else { 
    bar()
}
```

