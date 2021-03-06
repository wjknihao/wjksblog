---
title: hexo+github搭建个人博客
date: 2018-05-24 11:11:11
tags:
- 教程
- 程序猿
comment: true
---
欢迎来到我的hexo-github博客搭建教程。
# 环境配置
## node环境
- Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
- Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
- Node.js 的包管理器 npm，是全球最大的开源库生态系统。
浏览器打开[node](https://nodejs.org/en/)官网下载8.11.2版本的msi双击
### 环境测试
1.win+r 打开运行窗口，输入cmd回车
2.在cmd窗口输入
```
node -v
```
如果提示"node不是内部或外部命令"，需要重新安装node
如果提示v8.11.2则代表安装成功
## git服务 
- 浏览器打开[git](https://git-scm.com)官网，下载最新版的git安装
- 安装完毕后，在桌面右键菜单出现git bash here则代表安装成功
## 安装hexo脚手架
1,win+r打开运行窗口，输入cmd回车
2，在命令行输入 
```
npm install hexo-cil -g
```
通过npm包管理器全局安装hexo脚手架
#博客搭建
## 初始化博客项目
1，桌面右键git bash here 
2， 在命令行窗口输入：
```
hexo init blog
```
通过hexo在桌面新建一个叫blog的博客项目
ps：blog是项目名称，名字随意，但不能是中午
3,切换到bolg路径
```
cd blog
 ``
4,安装项目依赖
```
npm install
```
5.启动服务器
```
hexo s
```
6.预览博客
浏览器地址栏输入localhost:4000或者127.0.0.1:4000回车
ps：建议使用Chrome（谷歌浏览器）

## hexo 常规操作

- 清理项目缓存 
```
hexo clean
```
何时使用？
修改了博客内容却没有效果或者修复了bug报错依然存在
- 编译博客
```
hexo g
```
何时使用？
⑴每次hexo clean之后都需要重新编译
⑵部分情况下修改了_config.yml配置文件后需要重新编译
⑶手动新建博客文章之后需要重新编译
- 重启服务器
在之前启动服务的命令行窗口使用快捷键"ctrl+c"可以停止hexo服务
然后紧接着输入hexo s启动
何时使用？
修改了_config.yml需要重启服务
# heo项目托管到github
1，打开[git]()注册个人账户，并记录下用户了名和邮箱，并且验证邮箱
## 本机验证github的key
2.桌面右键打开git bush here 
```
ssh-keygen -t rsa -C "自己的邮箱"
```
一路回车，直到出现下列图案
+---[RSA 2048]----+
|..B = .          |
| * & =           |
|+ @ O   . .      |
|.* * o   = .  .  |
|  o o . S   +  E.|
|     o + . + .. o|
|      + + . . ...|
|     . + o .   .o|
|      . . +.    .|
+----[SHA256]-----+

接下来依次代开：c:/users/Administrator/.ssh路径
找到：id_rsa.pub文件右键选择记事本打开，全选并且复制里面的内容（key）
3，回到github页面，找到头像右侧倒三角下拉菜单，选择settings
4，在页面左侧选择ssj and gpk
5，点击右上角绿色 add ssh 按钮
6，在表单输入title(随意)和key(粘贴之前复制到的key)
然后点击绿色create ssh 按钮
7，回到刚才创建的key的命令行窗口验证用户名和邮箱
```
git config --global user.name "用户名"
git config --global user.email "邮箱"
```
如果验证成功，没有任何意思
## 创建github用户名同名仓库
在github页面点击头像右侧的+，选择 New repository
重点：仓库名必须是：用户名.github.io，PS:(严格区分大小写)如：wjknihao.github.io

## 配置hexo 
### 找到项目主目录下的_config,yml文件
在文档的最下方天剑如下内容
```
  type: git
  repository: https://github.com/用户名/用户名.github.io.git
  branch: master
```


PS：整个项目有两个_config.yml
根目录_config.yml负责整个项目的一些配置，如：博客名称、语言等
themes文件夹内的_config.yml负责主体样式方面的配置
## 项目推送
1.安装gcmw（解压压缩包，双击install.cmd)
2.打开博客项目根目录，右键git bush here
3,安装deployer-git依赖
```
npm install hexo-deployer-git --save
```
4，依次执行如下命令
```
hexo clean
```
```
hexo g
```
```
hexo d
```
5.中途会弹出github的验证，输入相应的应户名密码就好
如果推送成功，在浏览器打开http://用户名.github.io即可访问
