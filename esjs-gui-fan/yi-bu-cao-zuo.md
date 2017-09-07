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
 * @param {String} url 加载数据的 URL 地址
 * @param {Object} params 发送给服务器的数据
 * @param {Function} onSuccess 加载成功后的回调函数
 */
function load(url, params, onSuccess, onError) {
  let xhr = new XMLHttpRequest()
  
  xhr.timeout = 3000
  xhr.responseType = 'text'
  xhr.open('POST', url, true)

  xhr.ontimeout = function(e) { 
    if (typeof onError === 'function') {
      onError('timeout')
    }
  }
  
  xhr.onerror = function(e) { 
    if (typeof onError === 'function') {
      onError(e)
    }
  }
  
  xhr.onload = function(e) { 
    if(this.status === 200 || this.status === 304){
      if (typeof onSuccess === 'function') {
        onSuccess()
      }
    } else {
      onError()
    }
  }
  xhr.send(params)
}
```

使用上方定义的 load 函数加载数据：

```javascript
// 加载一个 URL
load('/api/foo', {id: 'xxxx'}, function(text) {
  console.log(`成功：${text}`)
}, function(err) {
  console.log(`失败：${err}`)
})

// 加载多个 URL
load('/api/bar', function(bar) {
  load('/api/bat', function(bat) {
    load('/api/baz', function(baz) {
      load('/api/foo', function(baz) {
          ... 
      })
    })
  })
})
```


***正确***

```javascript

/**
* 加载数据
* @param {String} url 加载数据的 URL 地址
* @param {Object} params 发送给服务器的数据
* @param {Function} callback 加载成功后的回调函数
*/
function load(url, params) {
  return new Promise((resolve, reject)=> {
    let xhr = new XMLHttpRequest()
    
    xhr.timeout = 3000
    xhr.responseType = 'text'
    xhr.open('POST', url, true)

    xhr.ontimeout = function(e) { reject('timeout error') }
    xhr.onerror = function(e) { reject(e) }
    xhr.onload = function(e) {
      if(this.status === 200 || this.status === 304){
        resolve(xhr.responseText)
      } else {
        reject()
      }
    }
    xhr.send(params)
  }
}
```

使用 Promise的 load 函数加载数据：

```javascript
// 加载一个 URL
load('/api/foo', {id: 'xxxx'})
.then(response=> {
  console.log('请求成功', response)
})
.catch(err=> {
  console.log('请求失败', err)
})

// 使用 await 调用 load 方法
try {
  let response = await load('/api/foo', {id: 'xxxx'})
  console.log(response)
} catch(err) {
  console.log(err)
}

// 并行请求多个方法
Promise.all([
  load('/api/foo'),
  load('/api/bar'),
  load('/api/baz'),
  load('/api/bat'),
]).then(results => {
  let [foo, bar, baz, bat] = results
})


// 串行请求多个方法
let foo = await load('/api/foo')
let bar = await load('/api/bar')
let baz = await load('/api/baz')
let bat = await load('/api/bat')