## HTML 命名规范

#### HTML5 规范中声明的所有标签和属性名称统一使用小写

*** 正确：***

```html
<div class=”wrapper”></div>
```
```html 
<section title=”foo”></section>
```

*** 错误：*** 

```html
<DIV class=”wrapper”></DIV> 
```
```html
<section Title=”foo”></section>
```

#### HTML5 支持自定义属性，自定义属性统一加上“data-”前缀

*** 正确： ***

```html 
<li data-price=“888”></li>
```

*** 错误：***
```html
<li price=”8888”></li>
```

#### 第三方的Vue 组件标签因为 Vue 官方支持包括大驼峰、小驼峰、羊肉串等不同的写法，不做强制规定，以后自主开发的 Vue组件标签名统一使用羊肉串写法，以前遗留的不规范写法逐步修改

```html
<template>
  <div>
    <product-selector />   // <= 建议写法
    <ProductSelector />   
  </div>
<template>

<script>
  import ProductSelector from ‘components/product-selector.vue’
</script>
```