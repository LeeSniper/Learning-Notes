# Choreographer

 协调动画、输入和绘制的时机。从显示子系统接收定时脉冲（例如 vsync 信号），然后安排显然下一个显示帧需要做的工作。应用通常不直接和 Choreographer 打交道，而是通过动画框架或者视图树更高级的接口，例如：
 
 - ValueAnimator.start()
 - View.postOnAnimation(Runnable)
 - View.postOnAnimationDelayed(Runnable, long)
 - View.postInvalidateOnAnimation()
 - View.postInvalidateOnAnimation(int,int,int,int)
 - View.invalidate()

保证 View 滑动流畅已经自动处理了。

公共方法：

- getInstance()
- postFrameCallback(FrameCallback) post 一个在下一帧执行的 callback，执行完一次自动 remove callback
- postFrameCallbackDelayed(FrameCallback, long)
- removeFrameCallback(FrameCallback)

只有具有 Looper 的线程才能获取 Choreographer，否则会抛出 IllegalStateException


常量：
USE_VSYNC，USE_FRAME_TIME，SKIPPED_FRAME_WARNING_LIMIT，MSG_DO_FRAME，MSG_DO_SCHEDULE_VSYNC，MSG_DO_SCHEDULE_CALLBACK，CALLBACK_INPUT，CALLBACK_ANIMATION，CALLBACK_TRAVERSAL，CALLBACK_COMMIT
成员变量：
Looper，FrameHandler，FrameDisplayEventReceiver，CallbackRecord，CallbackQueue[]