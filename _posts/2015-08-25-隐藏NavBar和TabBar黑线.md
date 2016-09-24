---
layout: post
title: 隐藏NavBar和TabBar黑线
description: // 在UITabBarController的viewDidLoad中添加这句代码[self.tabBar setValue:@(YES) forKeyPath:@"_hidesShadow"];
category: blog

---
###### 隐藏NavBar黑线
___
    // 在UITabBarController的viewDidLoad中添加这句代码
    [self.tabBar setValue:@(YES) forKeyPath:@"_hidesShadow"];

隐藏NavBar的底部黑线就用了个略侥幸的方法.这个方法需要使用runtime来替换UIViewController的viewDidLoad方法, 或者你可以在每个UINavigationController的rootViewController的viewDidLoad中添加下面这段代码, 总之下面这段代码需要用在UIViewController中才会有效果, 因为此时的UINavigationBar才算完成绘制和布局.

    // viewDidLoad for UIViewController
    - (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view.
    // 找出并隐藏navBar底部黑线
    UIImageView *shadowImageView = [self findHairlineImageViewUnder:self.navigationController.navigationBar];
        if (shadowImageView) shadowImageView.hidden = YES; // 存在便隐藏

        // your code...
    }

    // 找出一个view的子控件中高度小于等于1像素的UIImageView控件
    - (UIImageView *)findHairlineImageViewUnder:(UIView *)view {
    if ([view isKindOfClass:UIImageView.class] && CGRectGetHeight(view.bounds) <= 1.f) {
        return (UIImageView *)view;
    }
    for (UIView *subview in view.subviews) {
        UIImageView *imageView = [self findHairlineImageViewUnder:subview];
        if (imageView) {
            return imageView;
        }
    }
        return nil;
    }



