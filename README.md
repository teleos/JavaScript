# JavaScript

## 异步操作概述：

### 单线程

单线程模型是指，JavaScript只在一个线程上运行。 也就是说，JavaScript同时只能执行一个任务，其它任务都必须在后面排队等待。

`注意：` JavaScript只在一个线程上运行，不代表JavaScript引擎只有一个线程，事实上，JavaScript引擎有多个线程，单个脚本只能在一个线程上运行（称为主线程），其它线程都是在后台配合

### 异步任务和同步任务

程序里面所有的任务分为两类：`同步任务（sychronous）和异步任务（asynchronous）`。

同步任务是指没有被引擎挂起、在主线程上排队执行的任务。只有前一个任务执行完毕，才能执行另一个任务。

异步任务是那些被引擎放在一边，不进入主线程、而进入任务队列的任务。只有引擎认为某个异步任务可以执行了，该任务才会进入主线程执行。排在异步任务后面的代码，不用等待异步任务结束会马上运行，也就是说，异步任务不具有“堵塞”效应。

### 任务队列和事件循环

JS运行时，除了一个正在运行的主线程，引擎还提供一个任务队列（task queue）,里面时各种需要当前程序处理的异步任务。

首先主线程会去执行所有的同步任务。等到同步任务全部执行完，就会去看任务队列里面的异步任务。如果满足条件，那么异步任务就重新进入主线程开始执行，这时它就变成同步任务了。等到执行完，下一个异步任务再进入主线程开始执行。一旦任务队列清空，程序就结束执行。

### 异步操作的模式

1. 回调函数
2. 事件监听
3. 发布/订阅

## JS定时器

- setInterval()
- setTimeout()
- clearInterval()
- clearTimeout()
- 全局对象window上的方法，内部函数this指向window

## Promise 对象



## 查看滚动条距离

- window.pageXOffset/pageYOffset (IE8 及以下不兼容)
- document.body.scrollLeft/scrollTop （IE 8 及以下兼容）


## 查看视口的尺寸
- window.innerWidth/innerHeight (IE及IE8以下不兼容)
- document.documentElement.clientWidth/ClientHeight (标准模式下，任何浏览器都兼容)
- document.body.clientWidth/clientHeight (适用于怪异模式下的浏览器)

## 查看元素下的几何尺寸

- documentElement.getBoundingClientRect();
- 兼容性很好
- 该方法返回一个对象，对象里面有left、top、right、bottom等属性。left和top代表该元素左上角的x和y坐标，right和bottom代表元素右下角的x和y坐标
- height和width属性老版本IE并未实现
- 返回的结果并不是实时的。

## 让滚动条滚动

- window上有三个方法 ： scroll()、scrollTo()、scrollBy();
- 三个方法功能类似，用法都是将x、y坐标传入。即实现让滚动轮滚动到当前位置。
- 区别：scrollBy() 会在之前的数据基础上做累加。


## dom基本操作
- 查看元素尺寸dom.offsetWidth、 dom.offsetHeight
- 查看元素的位置 dom.offsetLeft、 dom.offsetTop
  - 对于无定位的父级的元素，返回相对文档的坐标。对于有定位的父级元素，返回相对于最近的有定位的父级的坐标

- dom.offsetParent 
  - 返回最近的有定位的父级，如无，返回body,body.offsetParent 返回null
- 脚本化css
  - 读写元素css属性
    - dom.style.prop
      - `可读写行间样式`，没有兼容性问题，碰到float这样的关键字，前面应加css    eg: float-->cssFloat
      - 复合属性必须拆解，组合单词变成小驼峰式写法
      - 写入的值必须式字符串格式

  - 查询计算样式
    - window.getComputedStyle(ele,null)  ;
    - 计算样式只读
    - 返回的计算样式的值都是绝对值，没有相对单位
    - IE8及IE8以下不兼容

  - 查询样式
    - elem.currentStyle
    - 计算样式只读
    - 返回的计算样式的值不是经过转换的绝对值
    - IE独有的属性


## 事件模型

### 事件的传播
一个事件发生后，会在子元素和父元素之间传播（propagation）。这种传播分为三个阶段。
  - **第一阶段** ：从`window`对象传导到目标节点（上层传到底层），称为“捕获阶段”（capture phase）。
  - **第二阶段** ： 在目标节点上触发，称为“目标阶段” （target phase）.
  - **第三阶段** ： 从目标节点传导会`window`对象（底层传回上层），称为“冒泡阶段”（bubbling phase）

### 事件的代理
由于事件会在冒泡阶段向上传播到父节点，因此可以把子节点的监听函数定义在父节点上，由父节点的监听函数统一处理多个子元素的事件。这种方法叫做事件的代理。

如果希望事件到某个节点为止，不再传播，可以使用事件对象的`stopPropagation`方法。

如果想要彻底取消该事件，不再触发后面所有click的监听函数，可以使用`stopImmediatePropagation`方法。

## Event对象

1. 概述
2. 实例属性
   1. Event.bubbles, Event.eventPhase
   2. Event.cancelable,Event.cancelBubble,event.defaultPrevented

