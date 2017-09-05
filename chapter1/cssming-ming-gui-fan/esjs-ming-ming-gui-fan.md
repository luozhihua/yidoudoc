# ES/JS 命名规范

## 1. 常量

统一使用全大写，单词之间使用下划线连接，CONSTACT_NAME

***实例：***

```javascript
    const API_HOST = '192.168.1.1'
```

## 2. 变量强制使用**小驼峰***（camelCased）

***正确：***

```javascript
    let onlineUsers = ['张三', '李四']
    let onlineUserList = ['张三', '李四']
```

***错误：***

```javascript
    let OnlineUser = ['张三', '李四']
    let online_user_list = ['张三', '李四']
```

## 3. 函数名、对象和类的方法名统一使用小驼峰（camelCased）

***正确：***

```javascript
    function getAllUsers(){
        return []
    }
    
    const user = {
        isExists() {
            return true
        }
    }
```

***错误：***

```javascript

    function get_all_users() {}
    
    function GetAllUsers() {}
    
    const user = {
        is_exists() {
            return true
        }
    }
```
    
## 4. 对象和类的属性名使用小驼峰（camelCased)
***正确：***

```javascript
    const user = {
        isExists: true,
        createdTime: 123124321543
    }
    
    class Clue extend Event {
        constructor() {
            super()
            
            this.createdTime = Date.now()
        }
        
        // 只读属性
        get createdTime() { return this.data.createdTime }
        
        // 可修改属性
        get updateTime() { return this.data.updateTime }
        set updateTime(time) { this.data.updateTime = time }        
    }
```

***错误：***

```javascript

    const user = {
        is_exists: true,
        created_time: 123124321543,
        _props: {...}
    }
    
    class Clue extend Event {
        constructor() {
            super()
            
            this.created_time = Date.now()
            this._user = Date.now()
        }
        
        // 只读属性
        get CreatedTime() { return this.data.createdTime }
        
        // 可修改属性
        get update_time() { return this.data.updateTime }
        set update_time(time) { this.data.updateTime = time }        
    }
```


5.  类名使用大驼峰（CamelCased）

正确：

class Distribution {
constructor(options) {
}
}

class UserCenter extend Event {
constructor(options) {
super()
}
}

错误：

class distribution {
constructor(options) {
}
}

class userCenter extend Event {
constructor(options) {
super()
}
}

6.  变量（函数）、类和对象的方法等，如果类型或者返回类型是 Boolean 的，名称加 is或 can前缀，类型是 Array的加 s 后缀或者 List 后缀

参考：
function isNumber(foo) { return (typeof foo === 'number'); }

export default {
methods: {
// 是否激活
isActivated (o) { return true },

// 是否可以删除
canDelete() { return false },
isCurrentTab() { return true }
getUsers() { return [{name:' 王路'}, {name:'小鱼人'}]; },
getOrderList() { return [{…}, {…}]; }
}
}