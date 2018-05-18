# 节点

node 类型
dom1级定义了一个Node接口，改接口将由DOM中的所有节点类型实现，这个Node接口在Javascript中式作为Node类型实现的，除了IE外，在其他所有浏览器中都可以访问到这个类型。

属性值                             |        nodeType   |       中文解释
-----                             |         ------    |       ------
ELEMENT_NODE                      |    1              |       Element类型
ATTRIBUTE_NODE                    |    2              |       Attr类型
TEXT_NODE                         |    3              |       Text类型
CATA_SECTION_NODE                 |    4              |
ENTITY_REFERENCE_NODE             |    5              |
ENTITY_NODE                       |    6              |
PROCESSING_INSTRUCTION_NODE       |    7              |
COMMENT_NODE                      |    8              |       Comment 类型
DOCUMENT_NODE                     |    9              |       Document 类型
DOCUMENT_TYPE_NODE                |    10             |       DocumentFragment 类型
DOCUMENT_FRAGMENT_NODE            |    11             |
NOTATION_NODE                     |    12             |


动态script

```js
//加载URL
function loadScript(url){
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src  = url;
    document.body.appendChild(script);
}
```

```js
//行内js
function loadScriptString(code){
    var script = document.createElement("script");
    script.type  = "text/javascript";
    try{
        script.appendChild(document.createTextNode(code));
    }catch(e){
        script.text = code;
    }
    document.body.appendChild(script);
}
```

动态加载css

```js
function loadStyles(url){
    var link = document.createElement("link");
    link.rel = "stylesheet";
    link.type = "test/css";
    link.href = url;
    var head  = document.getElementsByTagName("head")[0];
    head.appendChild(link)
}
```

```js
//内联样式
function loadStylesString(css){
    var style = document.createElement("style");
    style.type = "text/css";
    try{
        style.appendChild(document.createTextNode(css));
    }catch(e){
        style.styleSheet.cssText = css;
    }
    var head = document.getElementsByTagName("head")[0];
    head.appendChild(style);
}
```


querySelectorAll 方法相比 getElementsBy 系列方法有什么区别


1. W3C 标准

querySelectorAll 属于 W3C 中的 Selectors API 规范 [1]。而 getElementsBy 系列则属于 W3C 的 DOM 规范 。

2. 浏览器兼容

querySelectorAll 已被 IE 8+、FF 3.5+、Safari 3.1+、Chrome 和 Opera 10+ 良好支持 。getElementsBy 系列，以最迟添加到规范中的 getElementsByClassName 为例，IE 9+、FF 3 +、Safari 3.1+、Chrome 和 Opera 9+ 都已经支持该方法了。

3. 接收参数

querySelectorAll 方法接收的参数是一个 CSS 选择符。而 getElementsBy 系列接收的参数只能是单一的className、tagName 和 name

4. 返回值

querySelectorAll 返回的是一个 Static Node List，而 getElementsBy 系列的返回的是一个 Live Node List