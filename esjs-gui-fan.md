# ES/JS 规范

## 1. 模块化
#### 1.1. 使用 ES6  模块机制，import、export;

```javascript
export default {}
export default []
export default function(){}
export default class Distributor() {}
export default class Distributor extend Event() {}

import moment from 'moment'
import {isArray, isFunction} from 'lodash'
import * as _ from 'lodash'
```

#### 1.2. 一个文件只写一个模块
```javascript
/**
 * file: ./scripts/utils/time.js
 */
 
 import moment from 'moment'
 
 export default {
   /**
    * 获取当前时间戳
    * @public
    * @return {Number} 当前时间戳
    */
   now() {
     return Date.now()
   },
   
   /**
    * 格式化时间
    * @public
    * @param {String|Number} dataTime 日期时间字符串或时间戳
    * @param {String} [formatter='YYYY-MM-DD hh-mm-ss'] 格式
    * @return {String} 返回格式化后的时间字符串
    */
   format(dateTime, formatter='YYYY-MM-DD hh-mm-ss') {
     return moment(dateTime).format(formatter)
   }
 }
```

#### 1.3. 仅仅import当前模块所需要的方法和对象

```javascript
import {isArray, isFunction} from 'lodash'

let list = [1, 2, 3]
let plus = function(a, b) { return a + b }

if (isArray(list) && isFunction(plus)) {
    list.map((item, i) => {
        return plus(item, 10)
    })
}
```

#### 1.4. 不常用的模块使用异步导入
```javascript

import('lodash').then(lodash => { 
    let isArr = lodash.isArray([1, 2, 3])
    
    console.log(isArr)
})

```


## 2. 常量
#### 2.1. 使用 ES6 的 const 关键字声明常量，名称全大写
#### 2.2. 声明在文件或模块的最上方

## 3. 变量
#### 3.1. 所有变量必须先声明，后使用
#### 3.2. 使用 npm 打包的项目统一使用 let 声明变量，禁止使用 var 声明变量
#### 3.3. 变量声明全部放置在函数、方法的最前面
#### 3.4. 变量声明后空一行

## 4. 空格
#### 4.1. 逗号、===、!==、<、>、||、&&、+、-、*、/、等操作符前后必须留一个空格
#### 4.2. if、else、switch、function、class 关键字与后面的小括号或大括号之间必须留一个空格
#### 4.3. 函数和方法的参数之间必须留空格	