#异步操作

#### 禁止在任何场景下使用同步 ajax 请求

同步请求会造成页面阻塞，请求过程中不能响应用户的任何操作

#### 异步操作尽量使用 async/await 

```javascript

// 异步函数
async function load() {
  let url = '/api/xxx'
  let response = await axios.get(url)
  
  console.log(response)
}

// Vue组件
export default {
  data() {
    return {
      url: '/api/xxx',
      products: []
    }
  },
  
  /**
   * 加载数据的方法
   */
  async loadProducts() {
    let response
    
    try {
      response = await this.$ajax.get(this.url)
      
      this.prosucts = response.data
    } catch (error) {
      console.log(error.message)
    }    
  }
}
```