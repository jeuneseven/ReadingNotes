[如何实现 iOS App 的冷启动优化](https://blog.fiteen.top/2020/ios-app-launch-optimization)

* 热启动：App 进程还在系统中，无需开启新进程的启动过程
* 冷启动：App 不在系统进程中，如设备重启、手动 kill App 进程、长时间未打开，完整的 App 启动过程。

# 参考链接

[WWDC2016: Optimizing App Startup Time](https://developer.apple.com/videos/play/wwdc2016/406/)  
[WWDC2017: App Startup Time: Past, Present, and Future](https://developer.apple.com/videos/play/wwdc2017/413/)  
[优化 App 的启动时间](http://yulingtianxia.com/blog/2016/10/30/Optimizing-App-Startup-Time/)  
[今日头条 iOS 客户端启动速度优化](https://juejin.im/entry/5b6061bef265da0f574dfd21)  
[VasSonic 源码](https://github.com/Tencent/VasSonic)