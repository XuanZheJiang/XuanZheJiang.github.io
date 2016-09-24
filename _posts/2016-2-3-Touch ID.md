---
layout: post
title: Touch ID
description: 首先导入LocalAuthentication.framework库。然后写个方法来调用指纹解锁功能，方法内容如下......
category: blog

---
###### 首先导入LocalAuthentication.framework库。然后写个方法来调用指纹解锁功能，方法内容如下:
___

    //初始化上下文对象
    LAContext* context = [[LAContext alloc] init];
    //错误对象
    NSError* error = nil;
    NSString* message = @"Verify current Touch ID via Home Button.";
    //首先使用canEvaluatePolicy 判断设备支持状态
    if ([context canEvaluatePolicy:LAPolicyDeviceOwnerAuthenticationWithBiometrics error:&error]) {
    //如果支持则调用系统指纹验证
        [context evaluatePolicy:LAPolicyDeviceOwnerAuthenticationWithBiometrics localizedReason:message reply:^(BOOL success, NSError *error) {
            if (success) ｛
                //解锁成功 
            } else {
                [UIAlertView showAlertView:[error.userInfo objectForKey:NSLocalizedDescriptionKey] andMessage:nil];
                //在这里要说明一下，网上的教程通常都是通过错误代码枚举类型进行分类操作，但其实苹果公司是有对错误类型进行更新的，最好的办法就是直接显示[error.userInfo objectForKey:NSLocalizedDescriptionKey]，我在这是将其通过弹框进行显示错误信息。
            }
        }];
    } else {
        //不支持TouchID解锁
    }

