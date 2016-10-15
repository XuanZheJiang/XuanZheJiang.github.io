---

layout: post
title: Xcode8手动添加AFNetworking报警告
description: 警告内容：Conflicting nullability specifier on return types, 'nullable' conflicts with existing specifier 'nonnull'
category: blog

---
### Xcode8手动添加AFNetworking报警告
#####警告内容：  
Conflicting nullability specifier on return types, 'nullable' conflicts with existing specifier 'nonnull'

如图：
![](/images/Xcode8/Xcode8AFNetworking.png)  
解决办法：  
`nullable`和Xcode8的可空性的声明校验有冲突，尝试删除`nullable`即可。
![](/images/Xcode8/AFNetworking.png)

