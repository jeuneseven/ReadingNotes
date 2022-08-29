[深入解析 Flutter 下一代渲染引擎 Impeller](https://mp.weixin.qq.com/s/GptJbPXPediNRc4KvZzr6g)

# Impeller项目启动背景

* Impeller 未来将替代 Skia
* Flutter 团队彻底解决 SkSL（Skia Shading Language） 引入的 Jank 问题所做的重要尝试

## Jank 类型

### 首次运行卡顿(Early-onset Jank)

* 运行时着色器的编译行为阻塞了 Flutter Raster 线程对渲染指令的提交

### 非首次运行卡顿

