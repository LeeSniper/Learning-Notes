# SurfaceFlinger

创建 SurfaceFlinger 创建之后会初始化 MessageQueue，MessageQueue 创建内部类 Handler 对象，Handler 内部定义了三种 eventmask 类型：invalidate，refresh，transaction 针对这三种类型分别定义了对应的方法 dispatchRefresh()，dispatchInvalidate()，dispatchTransaction()。

初始化 SurfaceFlinger 
- 初始化 EGL 作为默认显示，EGLDisplay、
- 初始化 HWComposer 对象
- 获取 RenderEngine 引擎
- 检索创建的 EGL 上下文
- 初始化非虚拟显示屏（建立已经连接的显示设备，创建 BufferQueue 传入生产者和消费者，创建 FramebufferSurface（hwc, consumer），创建 DisplayDevice）
- 创建 EventThread，根据 vsync 偏移量是否一致，创建一个（sf-app）或者两个(app 和 sf) DispSyncSource 对应一个或者两个 EventThread
- 创建 EventControlThread
- 当不存在 HWComposer 时，使用软件 vsync

创建 HWComposer HWComposer 代表硬件显示设备，注册了 Vsync 回调。Vsync 本身是由显示驱动产生的，如果不支持硬件的 Vsync 则会创建 VsyncThread 线程来模拟定时 Vsync 信号。