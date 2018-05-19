## DOM 扩展

### Selector API Level 1
两个核心方法 querySelector(),querySelectorAll() 返回一个静态的NodeList对象


### 元素遍历

对于元素间的空格，IE9及之前的版本不会返回文本节点，而其他所有浏览器都会返回文本节点

Element Travresal API 为DOM 添加了以下五个属性：

childElementCount：返回子元素（不包括文本节点和注释）地个数

firstElementChild:指向第一个子元素 firstChild的元素版

lastElementChild : 指向最后一个元素， lastChild的元素版

previousElementSibling:指向前一个同辈元素，previousSibling的元素版

nextElementSibling 指向后一个元素 nextSibling的元素版


### HTML5

HTML5规范围绕如何使用新增标记定义了大量的JavascriptAPI ，其中一些API与DOM重叠，定义了浏览器应该支持的DOM扩展

getElementsByClassName() 原生具有极大性能优势

classList 属性

classList上的方法
- add(value):将给定的字符串值添加到列表中，如果值存在，就不添加了
- contains(value):表示列表中是否存在给定的值，如果存在则返回true,否则返回false
- remove(vlaue):从列表中删除给定的字符串
- toogle(value):如果列表中存在，则删除，否则添加



### HTMLDocument变化

readyState属性

    loading 正在加载文档
    complete 已经加载完文档

兼容模式检测
```js
if(document.compatMode === 'CSS1Compat'){
    // 标准模式 standard mode
}else{
    //怪异格式 quicks mode
}
```

插入标记

innerHTML 不要指望所有浏览器返回的innerHTML值完全相同

并不是所有元素支持innerHTML属性。不支持innerHTML属性的元素
```
<col> 、<colgroup>、<frameset>、<head>、<html>、<style>、<tabel>、<tbody>、<thead>、<tfoot>、<tr>
```


### scrollIntoView()

可以在所有的HTML元素上调用，给这个方法传入true做参数，或者不传参数，窗口滚动之后会让调用元素的顶部与视口顶部尽可能的平齐。传入false做参数，调用元素会尽可能全部出现在视口中。


### 专有扩展

文档模式

    <meta http-equiv="X-UA-Compatible" content="IE=edge">始终以最新的文档模式来渲染页面

children()

这个属性是HTMLCollection的实例,只包含元素中同样还是元素的子节点

在元素只包含元素子节点时，children和childNodes没有区别

contains()方法

```js
//通用contains函数
function contains(refNode,otherNode){
    if(typeof refNode.contains === 'function' && (!client.emgine.webkit || client.engine.webkit >= 522)){
        return refNode.contains(otherNode);
    }else if(typeof refNode.copareDocumentPosition === 'function'){
        return !! (refNode.compareDocumentPosition(otherNode) & 16)
    }else{
        var node = otherNode.parentNode;
        do{
            if(node === refNode){
                return true;
            }else{
                node = node.parentNode;
            }
        }while(node !== null)
    }

}

```

插入文本 innerText

由于不同浏览器处理空白符的方式不同，输出的文本可能会也可能不会包含原始HTML代码中的缩紧。

过滤所有HTML标签

ele.innerText = ele.innerText

类似属性textContent  DOM Level3中规定的一个属性
```js 
function setInnerText(ele,txt){
    if(typeof ele.textContent === 'string'){
        ele.textContent = txt;
    }else{
        ele.innerText = txt;
    }
}
```