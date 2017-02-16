---

layout: post
title: Notification
description: 
category: blog

---
### Notification

#### 监听一个通知主要需要4个对象来完成:
* Observer;
* NotificationName;
* Selector;
* Object; 

**Observer**是指由谁负责监听，**NotificationName**是指监听什么事件，**Selector**是监听到的信息由哪个方法来处理。如果是自己发消息，**Object**可以填入你想传送的数据,如果是监听系统消息，则不需要我们填入数据。可填入**nil**。  

获取传递过来的信息有2种方法，一种是**notification.userInfo**，另一种是**notification.object**。**userInfo**一般是系统消息，**object**则是你放入Object里的对象，你可以用**as**方法转换成需要的类型。



	// 发起广播位置信息
	NotificationCenter.default.post(name: NSNotification.Name.init(rawValue:"DiaryLocationUpdated"), object: self.address)
	
	// 监听广播位置信息
	NotificationCenter.default.addObserver(self, selector: #selector(updateAddress(_:)), name: NSNotification.Name.init(rawValue: "DiaryLocationUpdated"), object: nil)
	
	func updateAddress(_ notification: Notification) {
	        
	    if let address = notification.object as? String {
	        locationView.text = "于 \(address)"
	        locationHelper.locationManager.stopUpdatingLocation()
	    }
	        
	}