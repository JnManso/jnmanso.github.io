---
title: A lesson that every developer must know about multiple class cascade in CSS
date: 2012-03-01 21:30
category: 
author: 
tags: [css, developer, lesson, css, order, precedence]
summary: 
---

The text above was taken from <a href="http://css-discuss.incutio.com">http://css-discuss.incutio.com</a>

“What's the expected behavior when an element has multiple classes which redefine properties? Here's an example:
<pre class="brush: xml;">&lt;style type="text/css"&gt;  
  .headline { border: 3px solid red } 
  .newsitem { border: 2px solid red }  
  .blurb    { border: 1px solid red }
&lt;/style&gt;
...
&lt;h1 class="headline newsitem blurb"&gt;French Noblewoman Advocates Increased Cake Consumption Among Peasants&lt;/h1&gt;</pre>
Will the border of the H1 element be 3, 2, or 1 pixel wide?

To answer this question you need to understand how <a href="http://css-discuss.incutio.com/wiki/Selector_Specificity">Selector Specificity </a>works in CSS. In this case the (rough) answer is the "last highest-weighted rule wins", so the border will be 1px. <span style="color: #ff0000;">Note that it's the order of the rules in the stylesheet that controls which takes precedence; the order of the class names in the class attribute is irrelevant.”</span>