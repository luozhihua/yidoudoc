# 目录及文件命名

## 1. 统一使用羊肉串（kebab-case）写法

*** 正确：*** 
- `components/product-selector.vue`
- `components/follow-record/index.vue`

*** 错误：*** 
- `components/productSelector.vue`
- `components/followRecord/index.vue`

## 2. 目录命名原则

除项目结构外的目录，应该尽量以简短的业务模块名称命名，尽量用名词，不要含有无关的动词、修饰词或形容词

*** 正确：*** 
- `views/clue/bar.vue`
- `views/card-scanner/for.vue`

*** 错误：*** 
- `views/clueInfo/bar.vue`
- `views/scan-card/foo.vue`

## 3. 文件命名原则

文件名尽量以功能名称或操作名称命名，避免含有与上级目录名称相同的关键字词

*** 正确：***

- `views/clue/list.vue`

- `views/clue/edit.vue`

- `views/clue/add.vue`

*** 错误：***

- `views/clue/list.vue`

- `views/clue/edit-clue.vue`

- `views/clue/add-clue.vue`



