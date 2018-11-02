---
layout: post
title:  "封装2个类似jQuery的函数：addClass和setText"
date:   2018-11-02 16:20:58
categories: javascript 前端 jQuery
excerpt: 封装2个类似jQuery的函数：addClass和setText
---

* content
{:toc}

# 封装2个类似jQuery的函数：addClass和setText

先上代码

> 注：jQuery并不是这么写的

```js
window.jQuery = function(nodeOrSelector){
    let nodes = {}
    if(typeof nodeOrSelector === 'string'){
        let temp = document.querySelectorAll(nodeOrSelector)
        for(let i=0; i<temp.length; i++){
            nodes[i] = temp[i]
        }
        nodes.length = temp.length
    }else if(nodeOrSelector instanceof Node){
        nodes = {
            0: nodeOrSelector,
            length: 1
        }
    }

    nodes.addClass = function (className){
        for(let i = 0; i<nodes.length; i++){
          nodes[i].classList.add(className)
        }
    }
 
    nodes.setText = function(text){
        for(let i=0; i<nodes.length; i++){
            nodes[i].textContent = text
        }
    } 

    return nodes
}
window.$ = jQuery

var $div = $('div')
$div.addClass('red') // 可将所有 div 的 class 添加一个 red
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi
```

> 最根本的方法就是：`document.querySelectorAll(nodeOrSelector)`、`nodes[i].classList.add(className)`和`nodes[i].textContent = text`

给window对象加一个属性jQuery，它是一个函数，返回值为一个对象nodes。在里面要实现获取DOM，增加calss和设置textContent。最后面`window.$ = jQuery`是为了使用$，更简便，代码更少。

获取DOM是用`document.querySelectorAll(nodeOrSelector)`。这里判断参数是否是字符串。

增加class是用的`nodes[i].classList.add(className)`。

设置textContent是用的`nodes[i].textContent = text`。