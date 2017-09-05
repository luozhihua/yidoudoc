# 命名规范

所有命名尽量使用英文单词，若个别特有的中文名词可以使用拼音，英文不好可以借助翻译工具（有道词典或灵格斯都不错）

禁止在项目中使用数字或字母等表示序号的方式命名任何变量、文件名和目录，在公司业务中有特殊含义的、研发人员达成共识的除外（如 list1, list2 等）

## 目录及文件命名

#### 1. 统一使用羊肉串（kebab-case）写法

*** 正确：*** 
- `components/product-selector.vue`
- `components/follow-record/index.vue`

*** 错误：*** 
- `components/productSelector.vue`
- `components/followRecord/index.vue`

#### 2. 目录尽量以简短的业务模块名称命名，尽量用名词，不要含有无关的动词、修饰词或形容词

*** 正确：*** 
- `views/clue/bar.vue`
- `views/card-scanner/for.vue`

*** 错误：*** 
- `views/clueInfo/bar.vue`
- `views/scan-card/foo.vue`

#### 3. 文件名尽量以功能名称或操作名称命名，避免含有与上级目录名称相同的关键字词

*** 正确：***

- `views/clue/list.vue`

- `views/clue/edit.vue`

- `views/clue/add.vue`

*** 错误：***

- `views/clue/list.vue`

- `views/clue/edit-clue.vue`

- `views/clue/add-clue.vue`



