# JavaScript

## JS定时器

- setInterval()
- setTimeout()
- clearInterval()
- clearTimeout()
- 全局对象window上的方法，内部函数this指向window

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


