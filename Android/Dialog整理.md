[安卓基础] Dialog

安卓里面实现弹窗最基本的就是使用Dialog，但是还有AlertDialog，DialogFragment PopupWindow 等等，那么这些实现方式之间到底有什么区别的，各自又有哪些优缺点呢？这篇文章就先针对Dialog的基本用法，常见的需求，以及使用过程中可能出现的问题，做一个整理。

1、dialog基本用法


2、dialog常见需求


设置style

自定义layout，宽高

3、dialog常见问题

1、activity被销毁



2、不能使用application context


用activity实现dialog，WindowManager来实现

封装的第三方库

[afollestad/material-dialogs](https://github.com/afollestad/material-dialogs)

[pedant/sweet-alert-dialog](https://github.com/pedant/sweet-alert-dialog)

[orhanobut/dialogplus](https://github.com/orhanobut/dialogplus)

[sd6352051/NiftyDialogEffects](https://github.com/sd6352051/NiftyDialogEffects)


参考资料：

[Android Dialog API Reference](https://developer.android.com/reference/android/app/Dialog.html)

[WindowManager$BadTokenException](http://dimitar.me/android-displaying-dialogs-from-background-threads/)

[为什么Dialog不能用Application的Context](http://www.jianshu.com/p/628ac6b68c15)