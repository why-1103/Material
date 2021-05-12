以：<!DOCTYPE html> 开头
	<html>
	....
	</html>

绘制和缩放： viewport meta标签
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	device-width：设备宽度	initial-scale=1.0：缩放比例

通过为 viewport meta 标签添加 user-scalable=no 可以禁用其缩放（zooming）功能。
	maximum-scale=1.0 与 user-scalable=no 一起使用

响应式图像：添加 img-responsive class
	<img src="..." class="img-responsive" alt="响应式图像">
	如果需要让使用了 .img-responsive 类的图片水平居中，请使用 .center-block 类，不要用 .text-center。


全局显示、排版和链接：
	基本的全局显示:
	body {
  		font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  		font-size: 14px;
		line-height: 1.428571429;
		color: #333333;
 		background-color: #ffffff;
	      }

	排版：使用 @font-family-base、 @font-size-base 和 @line-height-base 属性作为排版样式。

	链接样式：通过属性 @link-color 设置全局链接的颜色。

bootstrap网格：
	有时候，我们不希望相邻的两个列紧靠在一起，但又不想用margin或者其他技术手段，这是可以用列偏移（offset）来实现。使用列偏移只需在列元素上添加类名.col-md-offset-*(星号代表要偏移的列组合数)，具有这个类名的列就会偏移，如：在列元素上添加.col-md-offset-4，表示该列向右偏移4个列的宽度

	*需要注意的是，使用col-md-offset-* 对列进行右偏移时，要保证列与偏移列的总数不超过12，不然会导致列断行显示