---
layout: post
title:  "HTML基础"
date:   2018-10-10 08:57:15
categories: html 前端
excerpt: HTML基础
---

* content
{:toc}

# HTML基础

HTML，中文“超文本标记语言”，英文“**H**yper**T**ext **M**arkup **L**anguage”，简称HTML，是一种用于创建网页的标准标记语言。

HTML可以嵌入JavaScript和CSS。维护HTML和CSS标准的组织为万维网联盟，即W3C。

W3C，中文“万维网联盟”，英文“**W**orld **W**ide **W**eb **C**onsortium”，又称W3C理事会，是万维网的主要国际标准组织。

W3C由蒂姆·伯纳斯-李于1994年10月离开CERN后成立，W3C试图透过W3C制定的心标准来促进业界成员间的兼容性和协议，试图让所有的供应商实施一套由联盟选择的核心原则和组件。从1997年开始，W3C在世界各地创建了区域办事处。2013年1月，北京航空航天大学成为W3C中国机构。

W3C制定的标准

* [W3C推荐标准](https://zh.wikipedia.org/wiki/W3C%E6%8E%A8%E8%8D%90%E6%A0%87%E5%87%86)
* [CSS](https://zh.wikipedia.org/wiki/CSS)：层叠样式表
* [DOM](https://zh.wikipedia.org/wiki/DOM)：文档对象模型
* [HTML](https://zh.wikipedia.org/wiki/HTML)：超文本标记语言
* [RDF](https://zh.wikipedia.org/wiki/%E8%B3%87%E6%BA%90%E6%8F%8F%E8%BF%B0%E6%A1%86%E6%9E%B6)：资源描述框架
* [SMIL](https://zh.wikipedia.org/wiki/SMIL)：同步多媒体集成语言
* [SVG](https://zh.wikipedia.org/wiki/SVG)：可缩放矢量图形
* [WAI](https://en.wikipedia.org/wiki/WAI)
* [Widgets](https://en.wikipedia.org/wiki/Widgets)
* [XHTML](https://zh.wikipedia.org/wiki/XHTML)：可扩展超文本标记语言
* [XML](https://zh.wikipedia.org/wiki/XML)：可扩展标记语言
* PICS：网上内容筛选平台

查看HTML、CSS、JavaScript文档可以去MDN。

MDN Web Docs（旧称Mozilla Developer Network、Mozilla Developer Center，简称MDN），是一个汇集众多Mozilla基金会产品和网上技术开发文档的免费网站，网址是https://developer.mozilla.org/zh-CN/

HTML标签列表

空标签是一个不可能存在子节点的标签，通常在一个空标签上使用一个闭标签是无效的。空标签包括：

* area
* base
* br
* col
* colgroup（span存在的时候）
* command
* embed
* hr
* img
* input
* keygen
* link
* meta
* param
* source
* track
* wbr

可替换标签不由CSS控制，是根据浏览器根据标签属性决定其显示的内容，包括：

* img
* object
* video
* textarea
* input
* audio
* canvas
* iframe
* embed
* option
* applet

下面是部分HTML标签

根元素

* html

文档元数据

* title
* base
* link
* meta
* style
* head

脚本

* script
* noscript
* template

章节

* body
* header
* footer
* nav
* section
* article
* aside
* address
* main
* h1 h2 h3 h4 h5 h6

组织内容

* p
    * paragraph，表示一个段落
* hr
* pre
* blockquote
* ol
* ul
* li
* dl
* dt
* dd
* figure
* figcaption
* div

文字形式

* span
* a
    * anchor
    * a标签可以创建一个到其他网页、文件、同一页面内的位置、电子邮件地址或任何其他URL的超链接。
    * href属性可以加一个超链接(http://baidu.com)、一个锚点(#abc)或者一个伪协议(javascript:alert(123);)
    * target属性可以添加_top(顶级窗口)、_blank(新窗口)、_parent(父级窗口)
* em
* b
* strong
    * 表示文本十分重要，一般用粗体显示。
* abbr
* small
* s
* cite
* q
* dfn
* data
* time
* code
* var
* samp
* kbd
* sub sup
* i
* u
* mark
* ruby
* rt
* rp
* bdi
* bdo
* br
* wbr

编辑

* ins
* del

嵌入内容

* img
* iframe
    * 可以将一个页面嵌入到当前页面，添加name属性的可以用a标签的href属性在iframe里打开页面
* embed
* object
* param
* video
    * 加上controls属性，可以允许用户控制视频的播放，包括音量，跨帧，暂停/恢复播放。
* audio
* source
* track
* canvas
* map
* area
* svg
* math

表格

* table
    * 表格。一般的结构如下
```
<table>
    <colgroup>
        <col>
        <col>
        <col>
    </colgroup>
    <thead>
        <tr>
            <th></th>
            <th></th>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td></td>
            <td></td>
            <td></td>
        </tr>
    </tfoot>
</table>
```
* caption
* colgroup
* col
* tbody
* thead
* tfoot
* tr
* td
* th

表单

* form
    * 目前一般用于提交post请求
    * 在form表单里添加`<input type="submit">`或者`<button>submit</button>`可以直接点击按钮提交
    * input等标签需要加name属性，用来提交数据到后台
    * Content-Type: application/x-www-form-urlencoded
* fieldset
* legend
* label
* input
* button
* select
* datalist
* optgroup
* option
* textarea
* keygen
* output
* progress
* meter

交互元素

* details
* summary
* menuitem
* menu