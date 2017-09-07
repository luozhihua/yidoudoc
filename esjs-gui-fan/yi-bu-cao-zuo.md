#异步操作

#### 1. 禁止在任何场景下使用同步 ajax 请求

同步请求会造成页面阻塞，请求过程中不能响应用户的任何操作

#### 2. 异步操作尽量使用 async/await 

```javascript

// 定义一个异步函数
function openSelector () {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(789)
    }, 5000)
  })
}

// 调用异步函数
async function load() {
  console.log('loading...');
  
  let response = await openSelector()

  console.log(`Response Data: ${response}`)
}

// Vue组件
export default {
  methods: {
    async loadProducts() {
      let url = '/api/xxxx'
      let response
      
      try {
        response = await this.$ajax.get(url)
        this.prosucts = response.data
      } catch (error) {
        console.log(error.message)
      }    
    }
  }
}

// 类方法
class Person {

}
```

#### 使用 Promise 代替 callback

使用callback会导致代码深层嵌套，逻辑混乱而复杂，同样也不兼容ES7的 async/await，要求使用 Promise 代替 callback

***错误***

```javascript

/**
 * 加载数据
 * 
 */
function load(url, params, callback) {

}