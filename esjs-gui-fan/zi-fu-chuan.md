#字符串

#### 1. ES和JS中使用 _单引号_ 代替 _双引号_

JS中统一使用单引号，这是大部分前端团队所执行的标准，绝大多数开源库和组件同样采用这一约定，需要注意的是JSON文件中必须使用双引号把 key 和 value 都包裹起来；

❌ ***错误***

```javascript
let userName = "乔峰"
let address = "上海市徐汇区桂平路xx号"
let button = "<button id=\"btn-add\" />"
```

✅ ***正确***

```javascript
let userName = '乔峰'
let address = '上海市徐汇区桂平路xx号'
let button = '<button id="btn-add" />'
```
#### 2. 在 ES6 中，应使用 _摸板字符串_ 代替 _字符串拼接_

ES6 支持模板字符串，比字符串拼接更直观、简洁

❌ ***错误***

```javascript
let categoryId = 'alksjf-zsjda-kjasdkhgaskdjsa'
let year = 2017
let month = 8
let url = '/api/clue?cate=' + categoryId + '&year=' + year + '&month=' + month

this.$ajax.get(url).then(...)
```
✅ ***正确***

```javascript
let categoryId = 'alksjf-zsjda-kjasdkhgaskdjsa'
let year = 2017
let month = 8
let url = `/api/clue?cate=${categoryId}&year=${year}&month=${month}`

this.$ajax.get(url).then(...)
```

#### 3. 省略每一行最后面的分号

❌ ***错误***

```javascript
let foo = 1;
let bar = 2;
let bat = 3;
let baz;

if (foo < 10) {
  baz = bar + bat;
} else {
  baz = bar - bat;
}
```

✅ ***正确***

```javascript
let foo = 1
let bar = 2
let bat = 3
let baz

if (foo < 10) {
  baz = bar + bat
} else {
  baz = bar - bat
}
```

#### 4. 数组、对象等元素最后建议不必跟一个逗号

为数组、对象加最后一个逗号，在ES中是被允许的，但是在部分IE版本中会抛出错误

👎 ***不建议***

```javascript
let users = [
  {name: '小人鱼'},
  {name: '小鱼人'},
  {name: '人小鱼'},
]

let details = {
  title: '精通 JavaScript 之 从入门到猝死',
  price: 200,
  author: '佚名',
}
```

👍 ***建议***

```javascript
let users = [
  {name: '小人鱼'},
  {name: '小鱼人'},
  {name: '人小鱼'}
]

let details = {
  title: '精通 JavaScript 之 从入门到猝死',
  price: 200,
  author: '佚名'
}
```