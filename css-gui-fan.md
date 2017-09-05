#CSS规范

## 1. 空格

**选择器**与`{`之间必须包含空格；**列表属性**写在单行时，“`,`”后必须跟一个空格

***错误：***

```css
    font-family:Aria,sans-serif;
```

***正确：***

```css
    font-family: Aria, sans-serif;
```

## 2. 行长度

2.1. 每行不得超过 120 个字符，除非单行不可分割。
2.2. 对于超长的样式，在样式值的 空格 处或“ ,”后换行，建议按逻辑分组。
2.3. 不同属性值按逻辑分组

    ```css
    background:
    transparent url(“./images/bg.png”)
    no-repeat 0 0;
    ```
2.4. 可重复多次的属性，每次重复一行

    ```css
    background-image:
        url(“./images/bg.png”)
        url(“./images/bg-2.png”);
     ```
## 3. 选择器

3.1. 如无必要，禁止为 id、class 选择器添加类型选择器，在性能和维护性上，都有一定的影响。
    
***错误：***
    
```css
    h1#page-title { … }
    footer.page-footer { … }
    ```
    
***正确：***
    
```css
    #page-title{ … }
    #page-footer{ … }
    ```

3.2. 选择器的嵌套层级尽量不大于 3 级，层级越深的限定条件越需要使用精确的选择器。

***错误：***

```css
    .page .header .login #username input {}
    .comment div * {}
```

***正确：***

```css
    #username input {}
    .comment .avatar {}
```

## 4. 属性值缩写

4.1. 在可以使用缩写的情况下，尽量使用属性缩写。

***建议：***

```css
    .post {
        font: 12px/1.5 arial, sans-serif;
    }
```

***不建议:***

```css
    .post {
        font-family: arial, sans-serif;
        font-size: 12px;
        line-height: 1.5;
    }
```

4.2. 使用 border / margin / padding 等缩写时，应注意隐含值对实际数值的影响，确实需要设置多个方向的值时才使用缩写。

border / margin / padding 等缩写会同时设置多个属性的值，容易覆盖不需要覆盖的设定。如某些方向需要继承其他声明的值，则应该分开设置。

***举个栗子：***
```html
    <article class="page"></article>
    
    <style>
        article { 
            margin: 5px; 
            border: 1px solid #999;
        }
    </style>
```

***正确：***
```css
    .page { 
        margin-right: auto; 
        margin-left: auto; 
    }
    .featured { border-color: #69c; }
```

***错误：***
```css
    .page { margin: 5px auto; }
    .featured { border: 1px solid #69c; }
```

## 5. 每个规则集之间保留一个空行

***正确：***

```css
    .selector1 {  display: block; width: 100px; }
    .selector2 {padding: 10px;  margin: 10px auto; }
    
    .another { color: red; }
```

***错误：***

```css
    .selector1 { display: block;  width: 100px; }
    
    .selector2 {  padding: 10px;  margin: 10px auto;}
    
    .another { color: red; }
```

## 6. 属性值

#### 6.1. CSS文本内容必须用双引号包围。

***正确：***

```css
    html[lang|="zh"] q:before {
        font-family: "Microsoft YaHei", sans-serif;
        content: "“";
    }
```

***错误：***

```css
    html[lang|=zh] q:before {
        font-family: 'Microsoft YaHei', sans-serif;
        content: '“';
    }
```

#### 6.2. 当数值为 0 - 1 之间的小数时，省略整数部分的 0

***正确：***

```css
    panel { opacity: .8 }
```

***错误：***

```css
    panel { opacity: 0.8 }
```

#### 6.3. url() 函数中的路径建议不加引号。

```css
    body { background: url(bg.png); }
```

## 7. 单位

#### 7.1. 尺寸单位必须使用 rem/vw/vh/% 等相对单位，严禁在移动页面的 css 中使用 px/pt 等单位

单位名称 |  描述
------- | --------
rem     | 相对于根节点`<html/>` 的 font-size，为了换算方便，`<html/>`的 font-size 默认设置为10px; 	
vw      | 相对于浏览器可视区域的宽度，50vw等于屏幕宽度的一半，100vw 等于整个屏幕的宽度	
vh      | 相对于浏览器可视区域的高度，50vh等于屏幕高度的一半，100vh 等于整个屏幕的高度	
%       | 用于宽度、高度以及 padding,margin 时，基于具有固定尺寸的上级元素	

***错误：***

```css
    h1 { font-size: 14px; }
    .dialog { width: 260px; } 
``` 

***正确：***

```css
    h1 { font-size: 1.4rem; }
    .dialog { width: 90vw; }
```

#### 7.2. 数值为 0 时必须省略单位。

***错误： ***

```css
    padding: 0px 5px;
```

***正确：***

```css
    padding: 0 5px;
```

## 8. 颜色

#### 8.1. RGB颜色值必须使用十六进制记号形式 #rrggbb，不允许使用 rgb()。

***正确：***

```css
    .success {
        box-shadow: 0 0 2px rgba(0, 128, 0, .3);
        border-color: #008000;
    }
```

***错误：***

```css
    .success {
        box-shadow: 0 0 2px rgba(0,128,0,.3);
        border-color: rgb(0, 128, 0);
    }
```

#### 8.2. 颜色值可以缩写时，必须使用缩写形式。

***正确：***

```css 
    background-color: #aca;
```

***错误：***

```css
    background-color: #aaccaa;
```

#### 8.3. 颜色值不允许使用颜色名称。

***正确：*** 
```css 
    color: #90ee90;
```

***错误：***
```css
    color: lightgreen;
```

#### 8.4. 颜色值中的英文字符统一小写。

***正确：***

```css
    background-color: #aca;
    color: #90ee90;
```

***错误：***

```csss
    background-color: #ACA;
    color: #90EE90;
```

## 9. 不需要为不同浏览器加不同前缀

-webkit-, -moz 等浏览器前缀在打包后会自动加上，只需要按照 CSS3 标准书写 css规则 即可；
 