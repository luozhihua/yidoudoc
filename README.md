# 一豆信息（上海）前端代码编写规范

- Version: v1.0
- Author:  罗志华
- 撰写日期：2017年9月

## 编辑器

* IntelliJ IDEA 和 Web Storm 请安装以下插件（安装方法自己Google、百度）：

  1. EditorConfig (**必须安装**)
  1. Vue.js (**必须安装**)
  1. ESLint (**必须安装**)
  1. Less support
  1. Sass Support
  1. scss-lint
  1. NodeJS


* Sublime Text 安装以下插件

  1. EditorConfig (必须安装)
  1. Vuejs Complete package （必须安装）
  1. JavaScriptNext ES6-Syntax (必须安装)
  1. EsFormatter
  1. CSS3
  1. https://github.com/luozhihua/sublime-vue-formatter （建议安装）

## 代码质量

对使用 NPM 打包的项目，将强制使用 ESLint 检测代码质量，此规范执行分两阶段执行：

#### 第一阶段：

开发人员自行启动带有 EsLint 的命令进行调试，有报错的即时解决

带 ESLint 的命令：

1. npm run dev:lint
1. npm run old:lint

#### 第二阶段：

1. 将会在提交代码时强制使用 ESLint 检查，一旦有不规范的代码，Git将自动拒绝合并
1. 在测试环境、生产环境的部署也将使用 ESLint 强制检查；
