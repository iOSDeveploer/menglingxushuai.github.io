---
layout: post
title: Quartz2D
date: 2016-01-03 
tag: iOS
---

Quartz2D是一个二维绘图引擎，同时支持iOS和Mac系统

### 用法

```objective-c
/*
 作用:专门用来绘图
 什么时候调用:当view现实的时候调用
*/
- (void)drawRect:(CGRect)rect {
     
//    NSLog(@"%s", __func__);
//    NSLog(@"%@", NSStringFromCGRect(rect));
     
    // 1.在drawRect方法中系统已经帮你创建了一个跟view相关联的上下文
    // 只要获取上下文就行了.
     
     
    // 1. 获取上下文
    CGContextRef ctx = UIGraphicsGetCurrentContext();
    // 2.描述路径
    UIBezierPath *path = [UIBezierPath bezierPath];
     
    // 画曲线
    // 2.1设置起点
    [path moveToPoint:CGPointMake(50, 280)];
    // 2.2添加一根曲线到某一个点
    [path addQuadCurveToPoint:CGPointMake(250, 280) controlPoint:CGPointMake(50, 50)];
    // 3.把路径添加到上下文
    CGContextAddPath(ctx, path.CGPath);
    // 4.把上下文的内容显示到View上
    CGContextStrokePath(ctx);
 
}
```

*注：只有在 - (void)drawRect:(CGRect)rect;方法中才有用

![](https://ws2.sinaimg.cn/large/006tNc79ly1fz9ghywkv9j3087088mx5.jpg)