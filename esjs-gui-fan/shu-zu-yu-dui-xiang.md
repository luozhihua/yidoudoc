#数组与对象

##### 禁止使用`new`关键字创建空数组和空对象

***错误***

```javascript
let list = new Array()
let params = new Object()
```

***正确***

```javascript

let list = []
let params = {}

```

#### ES6中数组循环请使用 foreach

***不建议***

```javascript
let list = [1, 2, 3, 4, 5]

for (let i = 0, len = list.length; i< len; i++) {
    list[i] = list[i] * 10
}
```

***建议***

```javascript
let list = [1, 2, 3, 4, 5]

list.forEach((item, i)=>{
    list[i] = item * 10
})
```

#### ES6中读取对象属性建议使用 Object.keys

