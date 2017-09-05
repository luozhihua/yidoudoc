# ES/JS 命名规范

#### 常量统一使用全大写，单词之间使用下划线连接，CONSTACT_NAME

实例：

```javascript
   const API_HOST = ‘192.168.1.1’
```

#### 变量使用小驼峰（camelCased） 

正确： 
-	let onlineUsers = [‘张三’, ‘李四’] 
-	let onlineUserList = [‘张三’, ‘李四’]

错误：

-	let OnlineUser = [‘张三’, ‘李四’] 
-	let online_user_list  = [‘张三’, ‘李四’]

3.	函数名、对象和类的方法名统一使用小驼峰（camelCased）

正确：

-	function getAllUsers(){}
-	{   
isExists() {
   return true
}
}
 错误：
-	function get_all_users() {}
-	function GetAllUsers() {}
-	{   
is_exists() {
   return true
}
}

4.	对象和类的属性名称统一使用小驼峰（camelCased），参考前一条
5.	类名使用大驼峰（CamelCased）

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

6.	 变量（函数）、类和对象的方法等，如果类型或者返回类型是 Boolean 的，名称加 is或 can前缀，类型是 Array的加 s 后缀或者 List 后缀

参考：
function isNumber(foo) { return (typeof foo === ‘number’); }

export default {
methods: {
		// 是否激活
		isActivated (o) { return true },

//  是否可以删除
canDelete() { return false }, 
isCurrentTab() { return true }
getUsers() { return [{name:’ 王路’}, {name:’小鱼人’}]; },
getOrderList() { return [{…}, {…}];  }
}
}