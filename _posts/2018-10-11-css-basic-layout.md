---
layout: post
title:  "CSS基础布局"
date:   2018-10-11 13:39:57
categories: css 前端
excerpt: CSS基础布局
---

* content
{:toc}

# CSS基础布局

### 左右布局

1、左边子元素加`float:left`，右边子元素加`float:right`，父元素加`clearfix`

```html
<main class="clearfix">
  <div class="left"></div>
  <div class="right"></div>
</main>
```

```css
.clearfix:after {
    content: '';
    display: block;
    clear: both;
}
.left{
    float:left;
}
.right{
    float:right;
}
```

2、flex布局

```html
<main>
    <div></div>
    <div></div>
</main>
```

```css
main{
    display: flex;
    flex-direction: row;
    justify-content: center;
}
main div{
    width: 100px;
    height: 100px;
    border: 1px solid red;
}
```

### 左中右布局

1、左右固定宽度，中间自适应

2、flex布局

```html
<main>
    <div></div>
    <div></div>
    <div></div>
</main>
```

```css
main{
    display: flex;
    flex-direction: row;
    justify-content: center;
}
main div{
    width: 100px;
    height: 100px;
    border: 1px solid red;
}
main div:nth-child(2){
    flex: 1;
}
```

### 水平居中

1、块级元素

`div`写上宽度，然后添加`margin:0 auto`

```css
div{
    width: 600px;
    margin: 0 auto;
}
```

2、内联元素

给父级元素加`text-align: center`

```html
<div><span>demo</span></div>
```

```css
div{
    text-align: center;
}
```

### 垂直居中

1、文字垂直居中，加同样的`height`和`line-height`

```css
div{
    height: 30px;
    line-height:30px;
}
```

2、文字垂直居中

```css
span{
    padding: 20px 0;
}
```

2、div垂直居中，flex布局

```html
<main><div></div></main>
```

```css
main{
    height: 500px;
    display: flex;
    align-items: center;
    border: 1px solid red;
}
main div{
    width: 200px;
    height: 200px;
    border: 1px solid red;
}
```

或者

```css
main{
    height: 500px;
    display: flex;
    flex-direction: column;
    justify-content:center;
    border: 1px solid red;
}
main div{
    width: 200px;
    height: 200px;
    border: 1px solid red;
}
```