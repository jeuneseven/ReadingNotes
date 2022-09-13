[YTKNetwork源码解析](https://juejin.cn/post/6844903487721963527)

# 架构

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2017/7/18/6cb2796ccc21db9117a0c672a4afdaf3~tplv-t2oaga2asx-zoom-in-crop-mark:3024:0:0:0.awebp)

# 设计模式

* YTKNetwork 使用命令模式（Command Pattern）

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2017/7/18/b9dd82db5499414a4fec275fef9e3a10~tplv-t2oaga2asx-zoom-in-crop-mark:3024:0:0:0.awebp)

# 源码解析

## 职责介绍

类  | 职责
------------- | -------------
YTKBaseRequest  | 请求类的基类。
YTKRequest  | YTKBaseRequest 子类。
YTKNetworkConfig  | 统一配置网络请求服务器、CDN等
YTKNetworkPrivate  | 
YTKNetworkAgent  | 单例，负责管理所有请求类。封装了 AFNetworking 
YTKBatchRequest  | 
YTKBatchRequestAgent  | 
YTKChainRequest  | 
YTKChainRequestAgent  | 
