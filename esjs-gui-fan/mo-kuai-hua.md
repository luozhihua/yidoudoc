# 模块化

#### 1. 使用 ES6  模块机制，import、export;

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

#### 2. 一个文件只写一个模块
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

#### 3. 仅仅import当前模块所需要的方法和对象

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

#### 4. 不常用的模块使用异步导入
```javascript

import('lodash').then(lodash => {
  let isArr = lodash.isArray([1, 2, 3])

  console.log(isArr)
})

```


