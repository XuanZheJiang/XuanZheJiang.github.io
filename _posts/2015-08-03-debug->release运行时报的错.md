---
layout: post
title: debug->release运行时报的错
description: ‘XXXX’ was compiled with optimization - stepping maybehaveoddly;variables may not be available
category: blog

---

`‘XXXX’ was compiled with optimization - stepping may behave oddly; variables may not be available`

之前上线的工程，现在加了功能运行的时候，就会报上面的错。在scheme中将`Run`的release改为debug就好了。


