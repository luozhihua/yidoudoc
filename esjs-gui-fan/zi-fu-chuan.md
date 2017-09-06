#字符串

#### 禁止使用双引号: `"`

JS中统一使用单引号，这是大部分前端团队所执行的标准，绝大多数开源库和组件同样采用这一约定

***错误***

```javascript
let userName = "乔峰"
let address = "上海市徐汇区桂平路xx号"
let button = "<button id=\"btn-add\" />"
```
***正确***

```javascript
let userName = '乔峰'
let address = '上海市徐汇区桂平路xx号'
let button = '<button id="btn-add" />'
```
#### 在 ES6 中，应使用 _摸板字符串_ 代替 _字符串拼接_

ES6 支持模板字符串，比字符串拼接更直观、简洁

***错误***

```javascript
let categoryId = 'alksjf-zsjda-kjasdkhgaskdjsa'
let year = 2017
let month = 8
let url = '/api/clue?cate=' + categoryId + '&year=' + year + '&month=' + month

this.$ajax.get(url).then(...)
```
***正确***

```javascript
let categoryId = 'alksjf-zsjda-kjasdkhgaskdjsa'
let year = 2017
let month = 8
let url = `/api/clue?cate=${categoryId}&year=${year}&month=${month}`

this.$ajax.get(url).then(...)
```