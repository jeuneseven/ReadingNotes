[如何实现 iOS App 的冷启动优化](https://blog.fiteen.top/2020/ios-app-launch-optimization)

* 热启动：App 进程还在系统中，无需开启新进程的启动过程
* 冷启动：App 不在系统进程中，如设备重启、手动 kill App 进程、长时间未打开，完整的 App 启动过程。