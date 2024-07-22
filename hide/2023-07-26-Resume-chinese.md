---
title: 简历
---

[Go to English version](https://chaojin101.github.io/posts/Resume-english/)

## 个人信息

- 郑潮劲/男/2002
- 本科/深圳大学计算机系
- [我的技术博客](https://chaojin101.github.io)/记录个人成长
- [我的 Github](https://github.com/chaojin101)/一些可复用的模块和练习项目

## 联系方式

- 邮箱/chaojin101@gmail.com
- 微信号/chaojin101
- 手机号/13510156183

## 工作经历

### 深圳科荔软件有限公司 （ 2022 年 9 月 ~ 2023 年 1 月 ）

#### 心愿墙项目

- 我负责后端开发，简单的 CRUD，后台注册的用户量大概 500~1000 左右。
- 根据产品的需求**设计数据库表**。
- **与前端协商 HTTP 接口的各个参数**。
- 阅读微信开发者文档，使用户通过微信登陆。

#### 编程登陆学校官网获取想要的信息

- 我负责研究校园网的登陆逻辑，为小程序用户提供查询课表，成绩等服务。
- 通过抓包发现校园网会将密码进行加密再发送给后台，测试后发现需要研究校园网是如何进行加密的才能成功登陆。
- 利用浏览器的调试工具，对校园网的 JavaScript 打断点，发现对密码使用了 AES 对称加密。
- 通过[流程图](https://static.179324.xyz/static/login-to-szu-flow-chart-827fdf2d-c63e-45f6-a46b-1c96390922b2.png)分析加密所需的参数及获取方式。
- 根据流程图编程实现登陆逻辑，成功获取想要的数据。

## 练习项目

### [http 包](https://github.com/chaojin101/http)

- 对 Go 官方的 http 包扩展。
- 比如，利用 post 请求向后台上传文件，我编写了一个[人性化的函数](https://github.com/chaojin101/http#httppostmultipart)。
- 这个包会持续更新，当我发现我需要的方法在官方包里找不到时，我会尽力更新，减少重复工作。

### [深大课程查询系统](https://szu-course.179324.xyz/docs)

- 手写 LRU Cache，实现了对课程信息的缓存，减少了对数据库的请求。
- 分析深大课程的请求逻辑，实现对全校课程的获取。
- 可以通过老师名字或课程名字查询课程，方便同学在选课系统关闭后，可以随时查询课程信息。

### [图片管理系统](https://gallery.179324.xyz/gallery)

- 已上线，完整，简单的全栈项目，用于熟悉前后端的开发流程。
- 学习使用 Swagger UI 对[后端接口文档](https://api.gallery.179324.xyz/docs)进行展示，提高了前后端开发效率。
- Web 前端使用了 Service Worker 和 Cache, 实现对不同资源使用不同的请求策略，加速了对资源的请求。
- 利用 Service Worker 和 Cache，实现了可以完全离线使用的功能。
- Web 前端实现图库幻灯片动画播放的功能。
- 我的 Service Worker 和 Cache 的学习笔记：[笔记](https://chaojin101.github.io/posts/web-service-worker/)

## 技能清单

- 对计算机基础知识有一定了解，学习过**数据结构与算法，操作系统，计算机网络**。
- 了解编程语言，在校期间上过**编译原理，程序语言设计(C)，面向对象编程(C++)，Java 程序设计课程**。
- 高中在编程社学过 Python，平时遇到的需求都是小需求，都能使用 Python 解决，因此**对 Python 相对比较熟悉**。
- 了解 SQL 语言，了解 MySQL 数据库和 PostgresSQL 数据库。
- **有测试的意识**，对稍微大的项目进行过单元测试，来方便后续功能的开发与重构。
- 跟着 [MDN 教程](https://developer.mozilla.org/en-US/docs/Learn)学习过 HTML，CSS，JavaScript，能够实现简单的前端页面。
- 跟着 [Vue 官方教程](https://vuejs.org/guide/introduction.html)学习过前端开发框架 Vue，提高了前端开发的体验和对项目的管理能力。
- 跟着 [Docker 官方教程](https://docs.docker.com/get-started/)学习过 Docker，了解 Docker 的基本概念。
- 了解 Linux 常用命令，能够对 Linux 下的程序进行管理。
- 了解 Git 基本操作，能够使用 Git 进行版本控制。
- 有一定的 CI/CD 经验，能够使用 Github Actions 进行自动化测试和部署。
- 有良好的英文阅读能力，能够阅读英文文档，已过英语四六级。

## 其它

- 在校期间获得[学习之星奖学金](https://static.179324.xyz/static/%E5%AD%A6%E4%B9%A0%E4%B9%8B%E6%98%9F-c0b92048-0884-4151-923f-18a4bda33783.jpg)。

---

## 致谢

感谢您花时间阅读我的简历，期待能有机会和您共事！
