---
layout: post
title: 在Photos中整合iPhoto及Aperture图片库
---

最近苹果发布了OS X 10.10.3，里面最让我兴奋的就是取代了iPhoto的Photos app。官方介绍[在此](https://www.apple.com/osx/photos/)。

在这次更新之前，我的图片库设置为：

* iPhoto: 储存iPhone, iPad拍摄的照片，随机存储的图片和墙纸等
* Aperture：储存以前单反/单电拍摄的照片

由于这次更新之后，[Aperture也从Mac App Store上下架了](http://www.macrumors.com/2015/04/10/iphoto-aperture-removed-mac-app-store/)，加上我已经很久没用Nex-5n拍照了，绝大部分出游拍照的需求iPhone 6 Plus都可以满足，所以考虑将两个图片库合并到Photos app里。

当10.10.3更新安装完成后，首次打开Photos用户可以选择任何一个图片库导入，但是无法多选。 所以问题来了，如果要合并多个图片库，应该怎么办？

经过一番研究之后，发现以下的方法更加方便和安全，具体步骤为：

1. 使用Photos导入iPhoto的图片库。官方提供了详细的[文档](https://support.apple.com/en-us/HT204478)介绍Photos是如何处理图片及其元数据的导入
2. 打开Aperture，选中所有的Projects，选择File菜单下的Relocate Originals
3. 选择导出目的地，文件夹及文件的命名规则，然后导出
4. Aperture会将所有Projects中的照片从图片库中导出为普通文件格式
5. 在Photos里，选择File菜单下的Import，导入所有Aperture的图片文件即可
