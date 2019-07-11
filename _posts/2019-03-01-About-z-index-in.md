---
layout:     post                    # 使用的布局（不需要改）
title:      About z-index           # 标题 
subtitle:   关于堆叠上下文小记            #副标题
date:       2019-03-01              # 时间
author:     smy                     # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - CSS
---

#### 那么到底什么情况下会产生堆叠上下文呢？其实堆叠上下文的生成主要受到元素的属性所影响。

如果任何一个元素满足一下条件之一，就会生成一个堆叠上下文。

- 文档的根元素（HTML）默认为一个堆叠上下文
- position值为"absolute"或"relative"，且z-index指定了除了auto以外值的元素
- position值为"fixed"或"sticky"
- 弹性布局的子元素，且z-index指定了除了auto以外值的元素
- opacity的值小于1的元素
- mix-blend-mode的值不是normal的元素
- 以下属性值不为"none"的元素
  1.transform
  2.filter
  3.perspective
  4.clip-path
  5.mask / mask-image / mask-border
- isolation值为"isolate"的元素
- -webkit-overflow-scrolling值为"touch"的元素
- will-change指定了除初始值以外的任何属性的元素
- contain值为"layout"/"paint"及含义其中之一的组合值的元素

#### 对于堆叠上下文我们需要知道以下几点：

- 在每个堆叠上下文内部，子元素的堆叠规则遵循上面所讲的基本规则。
- 堆叠上下文可以包含在其他堆叠上下文内部，它们会创建一个堆叠上下文层级结构。
- 堆叠上下文的层级结构与HTML的元素不同，因为对于没有创建堆叠上下文的元素会被父元素同化。堆叠上下文的层级只包括创建了堆叠上下文的元素。
- 堆叠上下文独立于其兄弟元素，在处理自身内部堆叠时，只考虑其后代元素。内部堆叠完成后，将当前堆叠上下文当成一个整体，考虑在父堆叠上下文中的堆叠顺序。通俗的说，子堆叠上下文的z-index值只在父堆叠上下文中有意义。
- 注意，第四条和文章开头提到的“z-index不能跨父元素比较”是不等价的，因为其限制了必须是堆叠上下文。

##### 参考文章
[https://mp.weixin.qq.com/s/7YPt5-9J46R83ouola0Trw](https://mp.weixin.qq.com/s/7YPt5-9J46R83ouola0Trw)