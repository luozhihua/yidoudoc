#常量与变量

## 1. 常量

#### 1.1. 使用 ES6 的 const 关键字声明常量，名称全大写
```javascript
const API_HOST = '127.0.0.1'
const API_PORT = '8080'
```
#### 1.2. 常量声明在文件、模块或代码块的最上方(如果有 import则在 import下方声明)
```javascript
import {isPlainObject} from 'lodash'

// 在 import后面声明常量
const USER_MODEL = {...}
```

```javascript
export default function () {
    // 在代码块的最前面声明常量（const下方空一行）
    const INTERVAL_TIME = 3000
    const USER_ID = 'akdf3h-fndnj-askdjal2312erflkeja9'
    
    setTimeout(()=>{
        console.log(Date.now())
    })
}
```

## 2. 变量
#### 2.1. 所有变量必须先声明，后使用

***错误****

```javascript
export default {
    async loadData() {
        url = 'https://www.yidouinc.com/api/v2.0/auth'
        parmas = {username: 'colin', password: '123456'}
        
        axios.post(url, params)
            .then((response)=>{
                console.log(response)
            })
    }
}
```

***正确***

```javascript
export default {
    async loadData() {
        let url = 'https://www.yidouinc.com/api/v2.0/auth'
        let parmas = {username: 'colin', password: '123456'}
        
        axios.post(url, params)
            .then((response)=>{
                console.log(response)
            })
    }
}
```

#### 2.2. 使用 npm 打包的项目统一使用 let 声明变量，禁止使用 var 声明变量

***错误***
```javascript
export default function (list = []) {
    var userNames = []
    
    for (var i = 0, len = list.length; i < len; i++) {
        userNames.push(list.userName)
    }
    
    return userNames
}
```
***正确***

```javascript
export default function (list = []) {
    let userNames = []
    
    for (let i = 0, len = list.length; i < len; i++) {
        userNames.push(list.userName)
    }
    
    return userNames
}
```

#### 2.3. 变量声明全部放置在函数、方法的最前面
***错误***
```javascript
export default class Customer extend Event () {
    constructor(id) {
        this.customerId = id
        this.load()
    }
    
    async load() {
        let id = this.customerId
        let url = '/api/customer/details/'
        url = api + id
        let data = await this.$ajax.get(url)
        let now = Date.now()
        
        data.records.forEach(record => {
            record.updateTime = now
        })
        
        this.customeName = data.name
        this.logo = data.imgUrl
    }
}
```

***正确***

```javascript
export default class Customer extend Event () {
    constructor(id) {
        super()
        this.customerId = id
        this.load()
    }
    async load() {
        let id = this.customerId
        let url = `/api/customer/details/${id}`
        let data = await this.$ajax.get(url)
        let now = Date.now()
        
        // ↑↑↑变量块后面空一行
        data.records.forEach(record => {
            record.updateTime = now
        })
        
        // 变量块后面空一行（上一行）
        this.customeName = data.name
        this.logo = data.imgUrl
    }
}

```

#### 2.4. 变量声明后空一行

参考上方第2.3节中的实例