# 换行和缩进

#### 1. 统一使用2个空格缩进

很多编辑器都可以把 tab 键自动转成空格，项目根目录下的'.editorconfig'文件就是用来统一不同编辑器的代码缩进和文件编码的，要求编辑器或 IDE启用对.editorconfig的支持（原生不支持的安装插件）

#### 2. 一行超过120个字符尽量拆分成多行

*** 错误：***

```javascript
if ((this.posibleClues.filter.orderType == 7 && this.posibleClues.list.length > 0 ) || (this.posibleClues.filter.orderType == 3 && this.posibleClues.list1.length > 0)) {
      return
}
```

*** 正确：***

```javascript
let possible = this. posibleClues
let type = possible.filter.orderType
let list = possible.list 
let clueList = possible.clueList

if ((type === 7 && list.length > 0) || (type === 3 && clueList.length > 0)) {
      return
}
```

#### 3. ES/JS/CSS禁止使用过深的嵌套结构

If/else 过深的嵌套可以拆分为多个小方法，AJAX 请求等异步操作可以使用 Promise 或 async/await 异步函数
CSS 嵌套结构过深会导致性能低下