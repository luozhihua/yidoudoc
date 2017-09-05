#HTML 规范

#### 1. 命名规范请参考第一节中的《[HTML命名规范](/chapter1/htmlming-ming-gui-fan.md)》

#### 2. 使用语义化标签

	***错误：***
	```html
	<div class=”header”>
		<div class=”title”></div>
	</div>
	
	<div class=”list”> 
		<div class=”list-item”>1</div>
		<div class=”list-item”>2</div>
		<div class=”list-item”>3</div>
	</div>
	```
	
	*** 正确：***
	
	```html
	<header>
		<div class=”title”></div>
	</header>
	
	<ul class=”list”> 
		<li class=”list-item”>1</li>
		<li class=”list-item”>2</li>
		<li class=”list-item”>3</li>
	</ul>
	```
	
#### 3. 属性值必须使用双引号

***错误：***
```html
<div id='user-list'></div>
```

***正确***
```html
<div id=”user-list”></div>
```

#### 4. HTML标签必须正确的关闭

非自关闭标签必须有对应的关闭标签，否则浏览器不能正确渲染页面；自关闭标签以“/>”结尾，虽然H5标准支持自关闭标签不带'/>'，但是不是所有浏览器都支持新特性；

***举个栗子：***

```html
<div>
	<img src=”” />       // 自关闭标签
	<input type=”number” />       // 自关闭标签
</div>
```

#### 5. 禁止在 HTML 标签上写样式

在 HTML 标签上写样式会很难维护和调试，Vue 组件中需要初始化的样式以:style=”styleObject”代替，styleObject 必须 在Vue组件中的data、computed或者 methods内定义为对象，把需要的样式全部至于其中；

*** 错误：***

```html
<div class=”clueDetails” style=”margin-bottom: 1rem; background-color: red;”></div>
<VueComponent :style=”{ color: 'red', fontSize: '1.4rem'}”
```

*** 正确：***

```html
<template>
	<div class=”component-a” :style=”customStyles”></div>
</template>
<script>
	export default { 
		data() {
			return {
				customStyles: { color: 'red', font: '2rem' }
			}
		}
 	}
</script>
```

_如果样式是可以预知的，更好的做法是全部在 css 中定义，然后通过在 JS 中通过不同的 class name 控制 HTML 节点的状态_

#### 6. Vue 组件模板中属性建议换行

Vue 组件的props、事件、directive（指令） 都是通过类似 HTML 属性的方式书写，但是因vue 组件的属性都是自定义属性，过长会造成阅读困难，超过两个建议每一个属性新启一行；

***建议：***

```html
<product-selector v-if="cond.type==='product'"
                  v-model="model[cond.key]"
                  :options="{selected: model[cond.key]}"
                  @click=”onClick”>
    <i class="yd-icon yd-grid"></i> 
    选择产品
</product-selector>
```

#### 7. 禁止在行内标签内嵌块状标签

行内标签嵌套块状标签会造成浏览器不能正确解析 HTML 树结构。

***错误：***

```html
<span>
    <div>Foo</div>
</span>

<a>
    <div>Bar</div>
</a>
```

***正确：***

```html
<div>
    <span>Foo</span>
</div>

<div>
    <a>Bar</a>
</div>
```

#### 8. input/button/textarea/select等原生表单元素必须设置 name 属性

原始表单提交会将表单元素的 name 属性值作为 key，特别是checkbox、radio含有多个选项的元素，如果不设置 name 会导致表单结果不正确；

***错误：***

```html
<form>
	<input type=”checkbox” id=”favoriteFruit” value=” 苹果”>
	<input type=”checkbox” id=”favoriteFruit” value=”西瓜”>
	<input type=”checkbox” id=”favoriteFruit” value=”橘子”>
</form>
```

***正确：***

```html
<form>
	<input type=”checkbox” name=”favoriteFruit” value=” 苹果”>
	<input type=”checkbox” name=”favoriteFruit” value=”西瓜”>
	<input type=”checkbox” name=”favoriteFruit” value=”橘子”>
</form>
```

#### 禁止在 tr/td/dl/li 等用于展示 list 的元素 上设置ID

这些元素大部门情况下会用于 JS循环渲染Array或 Map 结构的数据，很容易导致页面中出现含有相同ID 的元素，如果交互操作依赖这些相同的 ID会导致结果不符合预期；

如果在某些情况下一定要在循环中使用 ID，请保证 ID 的唯一性

*** 错误：***
```html
<ul>
	<% for (var i=0; i<list.length; i++) {% >
	<li id=”user”><%= list[i].username %></li>
	<% } %>
</ul> 

<template>
	<ul>
		<li v-for=”user in list” id=”user”>{{ user.nickname }}</li>
	</ul>
</template>
```

*** 正确：***

```html
<ul>
	<% for (var i=0; i<list.length; i++) {% >
	<li id=”user_<%= i %>”><%= list[i].username %></li>
	<% } %>
</ul>

<template>
	<ul>
		<li v-for=”(user, index) in list” :id=”'user'+ index”>
			{{ user.nickname }}
		</li>
	</ul>
</template>
```

#### Vue 模板中使用v-for的元素必须设置 :key 属性

请参考 [Vue官方介绍](https://cn.vuejs.org/v2/api/#key)
 