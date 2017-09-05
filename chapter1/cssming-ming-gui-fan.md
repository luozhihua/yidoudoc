# CSS  命名规范

#### 1. class name统一使用羊肉串写法

*** 正确：*** 
```html
<ul class=”clue-list”>
    <li></li>
</ul>
```

*** 错误：***
```html
<ul class=”clueList”>
    <li></li>
</ul>
```

#### 2. ID 统一使用羊肉串写法，尽量使用名词，按钮或有交互的节点 ID可以使用动词

*** 正确：*** 
```html
<button id=”btn-add-product”></button>```

*** 错误：***
```html
<button id=”btnAddProduct”></button>```

#### 3. DOM 节点的状态单独分离

能用 CSS 伪类实现的尽量用伪类实现，常见的状态：hover、focus、active、disabled、checked、hidden、visible、current，不要用类似 gray 表示disabled状态、blue表示current状态

*** 建议：***

```html
<div class=”wrapper hidden active checked”></div>
<style lang=”less”>
    .wrapper {
        padding: 1rem;
        
        &:hover { background-color: blue; }
        &:focus { box-shadow: inset 0 2px 2px rgba(0,0,0,0.1); }
        &.disabled { background-color: gray; }
        &.hidden { display: none; }
    }
</style>
```

#### 4. Class Name  根据不同类型使用容易理解的名称，

1. **表示状态尽量使用形容词或时态动词**，比如：complete（已完成 ），loading( 正在加载)

    *** 正确：***
    
    ```html
    <li class=”current”> 当前 Tab 头</li>
    <button class=”loading”>正在保存…</button>
    ```
    
    *** 错误：***
     
    ```html
    <li class=”blue”> 当前 Tab 头</li>
    <button class=”show-load-bar”>正在保存…</button>
    ```
        
2. **表示动作和交互的按钮、链接尽量使用动词或名词+动词**，如 btn-submit( 提交)；公共的含有动作交互类样式可以使用名词或形容词，如 btn-success、btn-primary

    *** 正确：***
    
    局部样式
    
    ```html
    <button class=”save”> 保存</button>
    <button class=”cancel”> 取消</button>
    <button class=”remove”> 移除</button>
    <button class=”submit”>  提交</button>
    ```
    
    全局样式
    
    ```html
    <button class=”btn-primary”>提交</button>
    <button class=”btn-default”>取消</button>
    ```
        
    *** 错误：***
    
    局部样式
    ```html
    <button class=”save-details”> 保存</button>
    <button class=”cancel-submit”> 取消</button>
    ```
    
    全局样式
    ```html
    <button class=”btn-submit”>提交</button>
    ```

3. **其他尽量用名词**，如：title、main、list、wrapper、navigator(nav)、menu 等，常见 CSS 命名参考文档最后的附件