#数组与对象

##### 1. 禁止使用`new`关键字创建空数组和空对象

❌ ***错误***

```javascript
let list = new Array()
let params = new Object()
```

✅ ***正确***

```javascript

let list = []
let params = {}

```

#### 2. ES6中数组循环请使用 foreach

👎 ***不推荐***

```javascript
let list = [1, 2, 3, 4, 5]

for (let i = 0, len = list.length; i< len; i++) {
  list[i] = list[i] * 10
}
```

👍 ***推荐***

```javascript
let list = [1, 2, 3, 4, 5]

list.forEach((item, i)=>{
  list[i] = item * 10
})
```

#### 3. 字面对象的每一个属性占一行

❌ ***错误***
```javascript

let params = { id: 'xxx', age: 30, contry: 'CN'}

```

✅ ***正确***

```javascript

let params = {
  id: 'xxx',
  age: 30,
  contry: 'CN'
}

```

#### 4. ES6中读取对象属性建议使用 Object.keys()

```javascript
let params = {
  userId: 'xxxxxxx',
  userName: '乔峰',
  password: '123456'
}

let keys = Object.keys(params) // => ['userId', 'userName', 'password']

Object.keys(params).forEach(key => {
  console.log(params[key])
})
```

#### 5. ES6 中 对象和类的方法可以省略 function 关键字

👎 ***不推荐***

```javascript
const utils = {
  format: function(params) {
    return `姓名：${params.name};`
  } 
}
```

👍 ***推荐***

```javascript
const utils = {
  parseUrl (url) {
    return url
  },
  
  format (params) {
    return `姓名：${params.name};`
  }
}
```