[Flutter Boost 混合开发框架初探](https://segmentfault.com/a/1190000039760722)

# 简介

* Flutter Engine负责线程管理、Dart VM状态管理以及Dart代码加载等工作，而Dart代码所实现的Framework则负责上层业务开发，如Flutter提供的组件等概念就是Framework的范畴。
* FlutterBoost 闲鱼技术团队开发的一个可复用页面的插件，旨在把Flutter容器做成类似于浏览器的加载方案。

# 架构

* 原生和flutter对于页面定义不同，原生指 ViewController 或者 Activity；flutter 指 widget，FlutterBoost 旨在统一混合工程中页面的概念，或弱化 flutter widget 对于容器页面的概念。

FlutterBoost 架构图：

![](https://segmentfault.com/img/remote/1460000039760724)

