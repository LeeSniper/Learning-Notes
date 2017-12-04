scaletype

是否缩放
是否等比例

填充方式

对齐方式




- center：图片放在view中心，但是不进行缩放。

- center_crop：等比例缩放图片，直到宽高都大于等于view的大小

- center_inside：等比例缩放，直到一个方向上等于view的大小


Matrix.ScaleToFit

- CENTER:等比例缩放，保证原图至少有一个方向完全符合view大小，居中
- END：等比例缩放，保证至少一个方向完全符合view大小，右下对齐
- FILL：拉伸缩放图片，以完全适应view大小
- START：等比例缩放，保证至少一个方向完全符合view大小，左上对齐




- fit_center：使用Center进行缩放

- fit_end：使用END进行缩放

- fit_start：使用START进行缩放

- fit_xy：使用FILL进行缩放

- matrix：使用矩阵变换进行缩放


参考资料

[ImageView.ScaleType](https://developer.android.com/reference/android/widget/ImageView.ScaleType.html)

[Matrix.ScaleToFit](https://developer.android.com/reference/android/graphics/Matrix.ScaleToFit.html#CENTER)