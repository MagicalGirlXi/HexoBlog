---
title: 如何加速自己博客的访问
date: 2020-03-06 21:44:56
tags: 
- 前端
- 建站
toc: true
categories: 萌新入门
thumbnail: https://blog-pics-1257119641.cos.ap-beijing.myqcloud.com/wallpaper-4897691_1280.png
---

## 引言

限制博客访问速度的瓶颈主要来自于

- 存储静态博客资源的服务器访问速度慢。
- 通过公有cdn取得一些样式文件时，由于国内没有高质量的节点导致获取速度慢甚至获取失败。（例如google-font和fontawesome）

<!--more-->

## 加速图片，视频等资源的加载速度

### 在无版权图片网站上获取图片链接，并插入网页中

例如，本文所使用的图片由<a href="https://pixabay.com/zh/users/enriquelopezgarre-3764790/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=4876720">enriquelopezgarre</a>在<a href="https://pixabay.com/zh/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=4876720">Pixabay</a>上发布

### 选择云服务商开通自己的OSS对象存储服务

#### 通俗地解释OSS对象存储

OSS对象存储服务，就是在服务提供商的服务器上开辟一块空间来存储你的任何文件，这些文件被称为“对象”，而服务商会提供这些文件的访问链接，便于你在任何地方访问他们，而这个过程是通过访问流量计费的，访问带宽是*不受限制*的。因此将一些较大的静态资源存储在OSS对象存储中，可以显著地提高网站的加载速度。

当然，作为一种云服务，对象存储服务还有更多强大的功能，便捷的使用方法。[腾讯云对象存储介绍](https://cloud.tencent.com/product/cos) [阿里云对象存储介绍](https://www.aliyun.com/product/oss?spm=5176.10695662.1112155.1.55fd30beKTMAci) 

#### OSS对象存储的简单使用

以腾讯云为例，首次开通可以免费使用六个月，每个月限制10GB流量。

注册开通服务后的简单使用步骤：

- 创建存储桶 [什么是存储桶](https://main.qcloudimg.com/raw/document/product/pdf/436_14102_cn.pdf)
- 上传文件到存储桶 [如何上传文件](https://main.qcloudimg.com/raw/document/product/pdf/436_14102_cn.pdf)
- 获取文件对应的访问地址，腾讯云上是`存储桶名称+分配的地址/文件名称`
- 把文件的访问地址引入到自己的网页中

#### 温馨提示

某些资源访问存在跨域问题，请在前端程序或对象存储服务中配置跨域的相关选项。

## 加速通用样式资源，JS文件等的加载速度

总体的思路也是配置CDN，用访问国内节点的资源替代，这里分享几个常用的站点

- [bootcdn稳定、快速、免费的前端开源项目 CDN 加速服务](https://www.bootcdn.cn/) 资源举例：vue, react, angular, jquery
- [css.loli.net 常用前端公共库 & 和谐使用 Google 公共库、字体库的方法](css.loli.net) 资源：CDNJS, Google公共库，Google-font, Gravatar 使用教程[烧饼博客](https://sb.sb/blog/css-cdn/) 