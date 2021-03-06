# UI组件之浮出层
[Demo](http://1039958384.github.io/IFE/task3/task3-1)

## 任务目的
* 练习综合运用HTML、CSS、JavaScript实现局部功能
* 练习对于代码的抽象与封装
* 为第四阶段的RIA任务做准备

## 任务描述
* 实现一个浮出层的UI组件
* 浮出层的中心默认在屏幕正中
* 当浮出层显示时，屏幕滚动时，浮出层始终保持位置固定在屏幕正中，不随屏幕滚动而变化位置。或者禁止页面在有浮出层出现时滚动
* 当浮出层显示时，点击浮出层以外的部分，默认为关闭浮出层。可以实现一个半透明的遮罩来挡住浮出层外的部分
* 浮出层的样式、内容和逻辑尽量解耦
* 提供使用JavaScript控制浮出层展现和关闭的接口
* 浮出层的窗口大小可以是一个默认固定值，也可以是随内容变化而自适应变化，也可以是通过接口参数进行调整，自行根据自己能力进行选择
* 有能力的同学可以实现浮出层的拖拽移动浮出窗口位置以及拖拽边缘来放大缩小浮出窗口的功能

## 任务注意事项
* 请注意代码风格的整齐、优雅
* 代码中含有必要的注释
* 可以合理选择使用其它第三方类库，但不建议

## 任务实现总结
### 弹出层的实现原理

* CSS处理:<br> 
> *  弹出层在文档中所有元素的前面,实现中将其 z-index 属性设为9999(position:absolute是前提)；<br>  
> *  而遮罩层在弹出层的后面,在其它所有文档元素的前面,因此实现中将其 z-index 属性设为了9998(position:absolute是前提)，并设置为半透明;

* JS处理: <br> 
> * 兼容性处理：获取滚动条、获取浏览器视口大小、得到DOM元素计算后的样式以及事件绑定和解绑都需要针对低版本IE做兼容性处理   <br>
> * 拖拽功能： 创建一个绝对定位的元素，使其可以用鼠标移动<br>
    (通过mousemove事件对象的 event.clientX 与 event.clientY 属性可以获得鼠标点击的坐标) - (mousedown事件的 event.clientX 与 event.clientY 属性可以获得拖拽开始时的鼠标坐标) = 鼠标移动的距离
> * 元素在视口中居中显示：<br>
    元素left = (视口宽度-元素宽度)/2 + 水平滚动条右移距离  <br>
    元素top = (视口高度-元素高度)/2 + 垂直滚动条下移距离   
> * mousedown 拖拽开始、mousemove 拖拽进行中、mouseup拖拽结束 事件的利用 <br>



