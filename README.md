# 前端应用开发架构

## 项目创建

### 脚手架

- IDE脚手架

  IDE或社区提供的脚手架

- 业务型脚手架

  根据业务特点通过Node写的工具，用于降低高频手写操作

### 通用组件

- Element UI
- Echart
- IView
- 项目分层组件

	- 错误数据采集
	- 业务代码与运行时框架隔离

		- 安全性兼容: setData
		- API访问缓冲: setData

	- 网络访问封装与管理

		- 访问主机运行时变更

	- 数据存储封装与管理
	- 日志统一收集

- 社区推荐组件

  https://ice.work/docs/guide/resource/npms

### 极速构建

- 飞冰

  极速构建企业级中后台前端应用
  https://ice.work/
  海量物料
  
  优势在于拥有强大的物料：
  涵盖：模板、区块、业务组件、基础组件
  可以通过拖拽快速组合各种页面。
  
  使用React开发，拥有特定的IDE，裁剪自VSCODE，这些组件目前还不能预览
  
  iceworks 内置了 ICE 官方模板帮助您快速创建一个中后台应用，并提供了 SCM 的支持（强大的 Git 集成）以加速发布操作。iceworks 还支持对接应用发布平台

	- 后台管理系统

	  快速预览：https://unpkg.com/@icedesign/pro-scaffold@3.0.15/build/index.html#/dashboard/monitor
	  
	  当项目庞大，单页面冗长，需要多团队开发时，可以考虑：icestark

## 编码

### 多人协作

- 编码规范

	- Airbnb JavaScript Style Guide

	  https://github.com/airbnb/javascript

	- 规范检查

	  配合ESLint执行

		- eslint
		- tslint
		- stylint
		- commitlint

	- 自动格式化

	  提交代码仓库时根据规范自动进行调整
	  按照团队统一的相关格式进行格式化，使提交到仓库的代码风格都是一致的

		- husky

		  https://github.com/typicode/husky#supported-hooks
		  https://git-scm.com/docs/githooks

- 分支管理

  Git Flow

	- 线上分支

	  该分支的最后一次commit总是目前生产环境所运行的稳定版本

	- 开发分支

	  所有的子分支都是从该分支检出
	  该分支的状态永远不落后于线上分支

	- 功能性开发分支

	  根据人员与功能所划分的功能版本开发分支
	  命名方式可以为：
	  分支类型/日期-姓名-功能
	  例如：
	  feature/20200202-Jim-performance-improve

	- 统一测试分支

	  有效利用小程序体验版只有一个的缺点
	  与测试分支相配合的还需要支持一个版本可以随时切换环境
	  这种特点在并行开发时效果尤为明显

### 脚手架

根据业务特性编写的脚手架
可以通过CLI的方式生成常用的小程序页面，并直接提供固定的页面模板与常用的页面模板，减少重复量，加速开发

### 组件化

- 业务组件
- UI组件
- 基础组件

### 自动编码工具

- 代码一键生成

  较为通用的前端解决方案，例如：HtmlFindClass

	- HtmlFindClass

- 业务组件一键生成

  与业务有强相关性，需要结合业务特点专门建造此类工具

### 编译

- 目标环境代码转换（Babel）
- 文件变更监控
- 编译结果缓存

  缩短单次编译时间，避免不必要的资源浪费，提升开发效率

- 编译/打包工具

	- Webpack
	- Rollup
	- Gulp
	- Grunt

### Mock

- 开发数据自动生成

  根据接口的数据接口自动生成测试数据

	- Mock.js

	  http://mockjs.com/

	- 随机数生成

		- Chance

		  https://chancejs.com/

- Mock平台

	- RAP2

	  http://rap2.taobao.org/
	  https://github.com/thx/rap2-delos

	- easy-mock
	- Api-mocker
	- eoLinker
	- fastmock

	  https://www.fastmock.site/#/

	- Mock.js

	  http://mockjs.com/

### 调试

- 控制台
- 网络
- 存储
- DOM

### IDE

- VS Code
- WebStorm

### 语言

- Html
- CSS

	- SASS/SCSS
	- LESS
	- POSTCSS

	  https://postcss.org/

- JS/TS

### 包管理

- 打包工具

	- NPM
	- YARN
	- CNPM

	  淘宝出品的npm镜像，很快

### 运行时框架

- Vue
- React

## 版本发布

### 代码压缩

- TreeShaking

  Tree-shaking, 也被称为 "live code inclusion," 它是清除实际上并没有在给定项目中使用的代码的过程，但是它可以更加高效。词汇来源查看https://medium.com/@Rich_Harris/tree-shaking-versus-dead-code-elimination-d3765df85c80#.jnypozs9n

### 混淆

### 分包

### 最小可执行单元

- 首屏公共库
- 必要业务代码

### 发布

- 平滑发布
- 增量发布
- 部署工具/系统

### 国际化

- 语言管理
- 内容管理

### 运行时环境分发

根据服务的用户环境预先生成各种运行时版本，依据环境获取对应的版本代码，例如通过Pollfill

### Html托管服务

极大缩短部署步骤与时间

- surge

  http://surge.sh/
  
  参考本架构部署示例：http://wooden-process.surge.sh/

- github pages

  https://pages.github.com/

- netlify

  https://www.netlify.com/
  
  几部就可以完成代码部署
  支持与Github，Gitlab强关联，可以读取仓库的分支，自定义配置编译脚本，非常方便，支持环境变量配置

### 云服务器

- DigitalOcean

  https://www.digitalocean.com/

## 测试回归

### 自动化测试

- 主链路测试（针对高频使用/功能复杂的模块）
- 接口自动化测试

	- 可以对各类环境进行配置性测试
	- 接口串行测试
	- 接口性能测试

		- 并发测试
		- 单接口访问时长

- ⾃动化测试沙盒

  通过模拟微信⼩程序运⾏环境和基础库 API，将⼩程序的运⾏和测试脱离微信环境，从⽽⽅便地对其进⾏⾃动化测试。最后通过拦截setData 接⼝及判断当前⻚⾯路由，对⼩程序运⾏结果进⾏校验

- 单元测试框架

	- Chai Assertion Library

	  用于JS测试的测试框架：https://www.chaijs.com/

### 手工测试

### 代码质量测试

lint类工具

## 版本控制

### 全量发布

包含版本回退能力

### 灰度发布

https://mp.weixin.qq.com/s/IT65m3VwlAhXusipB6wa2g

- 按百分比发布
- 按地域或特定人群发布

### 版本定义

- 代码版本管理
- 线上运行版本

### 运行时版本识别

- 肉眼随时可识别

## 质量监控及告警

https://mp.weixin.qq.com/s/HtxkwEVm8f1Ur1Il6JmEYQ

### 执行日志控制台

### 运行时性能数据采集与分析

### 业务日志采集

### 网络请求采集

- 接口响应率
- 接口响应速度
- 请求响应参数

### 脚本错误采集

分函数级与业务级

### 白屏化日志

### 业务异常采集

- 页面访问稳定率
- 页面测速
- 健康检查/存活监测

### 诊断能力

- 链路分析
- 错误聚类
- 函数流量回放

## 性能

### 监控

- 运行时性能数据采集
- 代码编译时长数据采集
- 小程序包体积数据采集

	- 分包情况下子包体积数据

- 接口响应时长数据采集
- 页面打开速度数据采集

  应用实时监控服务 ARMS
  
  https://www.aliyun.com/product/arms

### Faas网关

流量感知、HSF/HTTP触发器、限流

### 语言执行加速

- WebAssembly

### 性能监控与测试

- Sitespeed.io

  https://www.sitespeed.io/

	- 性能测试

		- Browsertime

		  https://www.sitespeed.io/documentation/browsertime/introduction/
		  
		  What is Browsertime good for?
		  
		  It is usually used for two different things:
		  
		  You run it as a standalone tool to collect performance timing metrics of your web site.
		  You integrate it in your tool as a JavaScript runner that collects whatever JavaScript metrics/information you want.

	- 性能数据比较
	- 网站监控

### 优化手段

- 首屏渲染时长

	- 骨架屏
	- 按需加载
	- 图片资源压缩

- 首屏响应时长

	- 资源缓存

	  https://www.cnblogs.com/laixiangran/p/8971119.html

		- expires
		- cache-control
		- Etag
		- Last-Modified

	- 资源压缩

	  单文件最小可运行单元，缩减空格与分号等

		- 文本压缩

			- Gzip

		- 图像压缩

			- 矢量图
			- 光栅化
			- 有损/无损压缩
			- Tinypng

	- 资源合并

	  多类资源合并为单个的Html/Css/Js，降低http链接次数与时间

	- 资源裁剪

	  缩减为首屏所需最小代码量

	- CDN静态资源加速

		- HTTP2

			- 权重
			- 多路复用

			  减少TCP握手时间

			- HTTPS安全加密
			- 无需等待

			  必要情况下，可以直接发送数据包，不需要等待缓存队列满的条件

			- 服务器推送
			- 头部压缩

			  https://link.jianshu.com/?t=https%3A%2F%2Fimququ.com%2Fpost%2Fheader-compression-in-http2.html

		- 缓存及版本管理
		- 最近访问节点
		- 负载均衡
		- 预热
		- 容灾

	- SSR

	  Server Side Render 服务侧渲染，有效降低网络传输时间，并且可以对渲染结果实施缓存策略，加速客户端呈现时间

		- Rax SSR

		  https://rax.js.org/ssr

## 数据统计

### 手工埋点

### 无痕埋点

### 业务数据指标

- PV/UV
- 漏斗数据
- 渠道转化

### 用户行为数据

- 流量分析

  查看全站流量状况，与历史进行比较，是涨是跌，哪个时段出了问题？出了问题需要排查。
  
  关注实时流量，如直播网站，趋势分析无法满足需要看当前在线。

- 来源分析

  来源分哪几类，分别带来多少流量？
  
  搜索引擎、外链的引入流量具体状况如何？

- 受访分析

  网站哪些内容受欢迎？？
  
  页面设计是否合理？

- 访客分析

  访客都是谁？
  
  访客的浏览行为是怎样的？

- 转化路径分析

  路径分析：根据您设置的特定路线，监测某一流程的完成转化情况，算出每步的转换率和流失率数据，如注册流程，购买流程等。

### 社区解决方案

- 友盟
- 阿里云

## DevOps

Auto DevOps provides pre-defined CI/CD configuration which allows you to automatically detect, build, test,
deploy, and monitor your applications.

### CI/CD

持续集成（Continuous Integration）
持续交付（Continuous Delivery）
持续部署（Continuous Deployment）

https://about.gitlab.com/stages-devops-lifecycle/continuous-integration/

https://mp.weixin.qq.com/s/k16SjTN7__iRB_7q78hldg

- Gitlab

	- 自动构建
	- 自动测试

	  代码质量分析：
	  https://docs.gitlab.com/ee/user/project/merge_requests/code_quality.html

	- 自动部署
	- 自动性能测试
	- 自主监控
	- Code Review

	  https://about.gitlab.com/stages-devops-lifecycle/code-review/

	- Review Apps

	  https://docs.gitlab.com/ee/ci/review_apps/index.html

## Node中间件

通过Node.js实现的网关层，可以整合各服务网关数据，实现按需配置请求，减少网络等待时间，加快网络请求时长，降低开发成本，在大型复杂的应用中效果尤为明显

按需获取数据常见的两种方案：
1.中台化服务
2.GraphQL

应该多关注稳定性，容灾容错，弹性，监控告警等

## 逆向分析

### JS

- js-beautify

  https://github.com/beautify-web/js-beautify

## 安全

### 数据安全

### 代码安全

### 通信安全

- SSL

  SSL, or Secure Sockets Layer, is the industry-standard technology for establishing an encrypted link between a web server and a browser.

## 跨平台开发

### Rax

https://rax.js.org/

- H5
- Weex

	- Android
	- iOS

- 阿里小程序
- 微信小程序

### Electron

## 跨域

http://www.ruanyifeng.com/blog/2016/04/cors.html

### 简单请求

- HEAD
- GET
- POST

### 非简单请求

非简单请求在发起请求前会发起预检，执行Opions的请求，如果预检通过，则本次生命周期内不会再进行预检

- PUT
- DELETE

## 常用工具推荐

https://ice.work/docs/guide/resource/tools

### FusionCool

Sketch设计辅助工具

### React Developer Tools

### Charles

### Postman

### Octotree

*XMind: ZEN - Trial Version*