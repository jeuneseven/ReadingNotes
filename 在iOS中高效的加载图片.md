[在iOS中高效的加载图片](https://juejin.cn/post/7019623908500324389)

# 图片的渲染流程

在iOS中使用 UIImage和UIImageView来记载图片，他俩遵守经典的MVC架构，UIImage相当于Model，UIImageView相当于View

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e6ebfb7f501e4647a8c27aedf35cec57~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp?)

UIImage负责加载图片，UIImageView负责渲染图片。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/678f901d47b54a03bfef3fb360833d24~tplv-k3u1fbpfcp-zoom-in-crop-mark:3024:0:0:0.awebp?)

