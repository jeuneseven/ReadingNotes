[YTKNetwork源码解析](https://juejin.cn/post/6844903487721963527)  
[YTKNetwork 使用基础教程](https://github.com/jeuneseven/YTKNetwork/blob/master/Docs/BasicGuide_cn.md)
[YTKNetwork 使用高级教程](https://github.com/jeuneseven/YTKNetwork/blob/master/Docs/ProGuide_cn.md)

# 架构

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2017/7/18/6cb2796ccc21db9117a0c672a4afdaf3~tplv-t2oaga2asx-zoom-in-crop-mark:3024:0:0:0.awebp)

# 设计模式

* YTKNetwork 使用命令模式（Command Pattern）

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2017/7/18/b9dd82db5499414a4fec275fef9e3a10~tplv-t2oaga2asx-zoom-in-crop-mark:3024:0:0:0.awebp)

场景  | Command | ConcreteCommand | Invoker | Receiver | Client
------------- | ------------- | ------------- | ------------- | ------------- | -------------
餐厅 | 空白订单 | 填入菜名的订单 | 服务员 | 厨师 | 客人
YTKNetwork | YTKBaseRequest | CustomRequest | YTKNetworkAgent | AFNetworking | ViewController/ViewModel

# 源码解析

![](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2017/7/18/8850c711921aa88ed065388b3a910c36~tplv-t2oaga2asx-zoom-in-crop-mark:3780:0:0:0.awebp)

## 职责介绍

类  | 职责
------------- | -------------
YTKBaseRequest  | 请求类的基类。持有 NSURLSessionTask 实例，responseData，responseObject，error等，提供需要子类实现的网络请求方法，处理代理和 block，让 YTKNetworkAgent 发起请求。
YTKRequest  | YTKBaseRequest 子类。处理缓存。
YTKNetworkConfig  | 统一配置网络请求服务器、CDN等。
YTKNetworkPrivate  | 提供工具方法；给 YTKBaseRequest 增加分类。
YTKNetworkAgent  | 单例，负责管理所有请求类。封装了 AFNetworking，负责发起、结束请求，持有字典存储正在执行的请求。
YTKBatchRequest  | 批量请求，维护一个数组保存请求类，遍历数组发起请求，有一个请求失败，则数组中的请求都失败。
YTKBatchRequestAgent  | 持有数组管理多个 YTKBatchRequest，支持添加删除请求。
YTKChainRequest  | 链式请求，维护一个数组保存所有请求类，一个请求结束才发起下一个请求，如果有一个失败，则数组中的请求都失败。
YTKChainRequestAgent  | 持有数组管理多个 YTKChainRequest，支持添加、删除 YTKChainRequest。

## 基础功能



## 高级功能

### YTKUrlFilterProtocol

* 用于对网络请求增加参数（版本号等）或修改路径。