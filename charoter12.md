# DOM2和DOM3

#### DOM变化

确定文档所属窗口
```js
var parentWindow = document.defaultView() || document.parentWindow;
```

DOM3中比较节点

isSameNode()  和  isEqualNode() 接受一个节点参数，并在传入节点与引用的节点相同或相等时返回true。所谓相同是指的两个节点的引用同一个节点。所谓相等，指的是两个节点具有相同的类型和相等的属性

获取iframe窗口对象

```js
var iframe = document.getElementById('iframe');
var iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
```
访问框架或内嵌框架的文档对象要受到跨域安全策略的限制。


### 样式

DOM2级样式为style对象定义了一些属性和方法

- cssText 能够访问到style特性中的css代码
- length 应用给元素的css属性的数量
- parentRule  表示css信息的CSSRule对象
- getPropertyCSSValue(propertyName) 返回包含给定属性值的CSSValue对象
- getPropertyPriority(propertyName) 给定属性使用了!important ,返回true,否则空字符串
- getPropertyValue(propetyName) 返回给定属性的字符串值
- item(index) 返回给定位置的CSS属性名称
- removeProperty(propertyName) 从样式表中删除给定属性
- setProperty(propertyName,value,priority) 将给定属性设置为相应的值，并加上优先权标志 !important或者空字符串

获取相应的样式
```js
function getStyleValue(ele,str){
    if(window.getComputeStyle){
        return window.getComputeStyle(ele)[str];
    }else{
        return ele.currentStyle[str];
    }
}
```

元素大小

偏移量

- offsetHeight : 元素的高度、（可见的）水平滚动条高度、上下边框高度
- offsetWidth:元素的宽度、（可见的）垂直滚动条宽度、左右边框宽度
- offsetLeft : 元素的左外边框至包含元素的左内边框之间的像素距离
- offsetTop : 元素的上边框至包含元素的上内边框之间的像素距离

客户区大小

- clientWidth 元素内容区宽度加左右内边距的宽度
- clientHeight 元素内容区高度加上下内边距高度

```js
//获取视口大小
function getViewport(){
    if(document.compatMode == 'BackCompat'){
        return {
            width:document.body.clientWidth,
            height:document.body.clientHeight
        }
    }else{
        return {
            width:document.documentElement.clientWidth,
            height:document.documentElement.clientHeight
        }
    }
}
```

滚动大小

- scrollHeight 在没有滚动条的情况下，元素内容的总高度
- scrollWidth 没有滚动条的情况下，元素内容的总宽度
- scrollLeft 被隐藏在内容区左侧的像素数
- scrollTop 被隐藏再内容区上方的像素数
