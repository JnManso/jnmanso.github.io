---
title: Disabling an element in jQuery 1.6
date: 2011-08-11
categories: Blog
tags: Programming
---

Last week, After upgrading a project from jQuery version 1.5.2 to 1.6.2. I encountered some problems disabling elements with the release of jQuery 1.6. The recommendation for disabling elements changed.  We need to start using prop() method before we use attr().

So, is necessary to substitute

```javascript
$(''.control'').attr(''disabled'', ''disabled'');
$(''.control'').removeAttr("disabled");
```

with

```javascript
$(''.control'').prop(''disabled'', ''disabled'');
$(''.control'').removeProp("disabled");
```