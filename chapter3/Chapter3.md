
# 写在前面

2018年2月份入手了《css世界》一书。打算过年内看完，但是翻阅之后决定作为工具书多次阅读并记笔记总结之，加深自己对css的理解（源于我看第五章的时间线拉的比较长，几乎每次都要重头过一遍）当然最好要回归实践，否则理论永远只是理论。  
回想自己刚上手写css的时候先引入一段重置css然后再引入boostrap·css。随着页面越来越个性化，我发现写一段易修改，可维护，代码量少的css相当重要。

# 3 流、元素、基本尺寸
## 3.1 块级盒子（认识各种盒子）
根据整个第三章第四章以及第五章的内容我把盒子模型之间的关系画了一个总的示意图。 
## 3.2 width/height 作用的具体细节
### 3.2.1 width:auto属性
  
*  充分利用可用空间 `<div`> ,`<p>`这些元素默认宽度100%充满父级 （外部尺寸）

* 收缩与包裹性  （内部尺寸）

* 收缩到最小 （内部尺寸）

* 超出容器限制 （内部尺寸）

###   “外部尺寸”与“内部尺寸” 
 
   外部尺寸：宽度由外部元素决定  
   内部 尺寸：宽度由内部元素决定 如果一个元素里面没有内容宽度为0 那么这个元素应用的就是“内部尺寸”

###   内部尺寸与流体特性

 1. 包裹性的例子 :按钮元素`button`具体表现为按钮文字越多宽度越宽。但是文字足够多，则会在容器的宽度处自动换行。PS按钮元素的最大宽度为240px。除了inline-block元素，**浮动元素**以及**绝对定位元素**都具有包裹性。

 2. 首选最小宽度

 3. 最大宽度 实际等同于“包裹性”元素设置white-space:nowrap声明后的宽度。如果内部没有块级元素或者块级元素没有设定宽度值，则“最大宽度”实际上是最大的连续内联盒子的宽度

 ### 3.2.2 width值作用的具体细节
 width作用在content box上
 ### 3.2.3 CSS流体布局下的宽度分离原则
 不在同一层标签上设置width,padding。 width设置在父级标签上，子级标签设置padding,border属性。子级自适应父级宽度。

 ### 3.2.4 改变width作用细节的box-sizing

 box-sizing被发明的初衷更大的可能是解决替换元素宽度自适应问题。原因替换元素的尺寸由内部元素决定对于其设置display属性是inline还是block,替换元素的宽度都不会受其影响。
 textarea的width100%自适应父级，同时保留border,padding属性只能通过`box-sizing:border-box`来解决
 ```
 input ,textarea, img, video, object {
            box-sizing: border-box
        }
 ```
### 3.2.5 height:auto
`height:auto`也有外部尺寸特性，仅存在于绝对定位模型中，也就是“格式化高度”。
### 3.2.6 height: 100%
如何让元素支持height:100%?  
1. 设定显示的高度
``` css
  html, body {
    height: 100%;
}
```

2. 使用绝对定位 (备注绝对定位元素百分比计算和非绝对定位元素的百分比计算是有区别的，区别在于绝对定位的宽高百分比计算是相对于padding box)
``` css
.box {
    position: absolute;
    width: 100%;
    height: 100%;
}
```
## 3.3 CSSmin-width/max-width和min-height/max-height

### 3.3.2 与众不同的初始值
min-width/min-height的初始值为auto  
max-width/max-height的初始值为none (思考为什么max的初始值为none 而不是auto)

### 3.3.3 超越!important 超越最大

简单的来说min和max的权重比!important大。 如果min和max设置起冲突的时候。min-width 会覆盖max-width。
