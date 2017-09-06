#条件与判断

## 禁止使用`==` 和 `!=`

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

let bat = false
if (bat == null) {
    console.log('bat is null')
} else {
    console.log('bat is not null')
}

```