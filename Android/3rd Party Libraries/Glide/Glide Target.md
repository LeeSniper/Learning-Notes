glide target


Hierarchy For Package com.bumptech.glide.request.target

Package Hierarchies:
All Packages
Class Hierarchy


- com.bumptech.glide.request.target.BaseTarget<Z> (implements com.bumptech.glide.request.target.Target<R>)
	- com.bumptech.glide.request.target.SimpleTarget<Z>
		- com.bumptech.glide.request.target.AppWidgetTarget
		- com.bumptech.glide.request.target.NotificationTarget
		- com.bumptech.glide.request.target.PreloadTarget<Z>
	- com.bumptech.glide.request.target.ViewTarget<T,Z>
		- com.bumptech.glide.request.target.ImageViewTarget<Z> (implements com.bumptech.glide.request.transition.Transition.ViewAdapter)
			- com.bumptech.glide.request.target.BitmapImageViewTarget
			- com.bumptech.glide.request.target.DrawableImageViewTarget
			- com.bumptech.glide.request.target.ThumbnailImageViewTarget<T>
				- com.bumptech.glide.request.target.BitmapThumbnailImageViewTarget
				- com.bumptech.glide.request.target.DrawableThumbnailImageViewTarget
- android.graphics.drawable.Drawable
	- com.bumptech.glide.request.target.FixedSizeDrawable
- com.bumptech.glide.request.target.ImageViewTargetFactory

Interface Hierarchy

- com.bumptech.glide.manager.LifecycleListener
	- com.bumptech.glide.request.target.Target<R>
- com.bumptech.glide.request.target.SizeReadyCallback

- BaseTarget

抽象类

- SimpleTarget

- ViewTarget

- ImageViewTarget

- FixedSizeDrawable

- appwidgettarget
- bitmapimageviewtarget
- bitmapthumbnailimageviewtarget
- drawableimageviewtarget
- drawablethumbnailimageviewtarget


- imageviewtargetfactory
- notificationtarget
- preloadtarget

- thumbnailimageviewtarget
