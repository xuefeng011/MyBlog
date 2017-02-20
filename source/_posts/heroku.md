---
title: heroku
date: 2016-10-12 09:45:34
tags: [Server]
categories: Server
---

Heroku 免费云空间

<!-- more -->
-----


## 准备
    必须要用git
## 注册账户
[hero官网](https://www.heroku.com)




## 安装Heroku Toolbelt
[Heroku Toolbelt](https://toolbelt.heroku.com/)

  Heroku Toolbelt是用于创建、管理Heroku上apps的命令行工具

**heroku** 的命令行客户端将被安装到`/usr/local/heroku`，同时，``/usr/local/heroku/bin``将被添加到你的PATH环境变量

下载并安装完成后，在 shell 中输入`heroku login`，用创建`heroku`账号的`email`和`密码`登陆
```
    $ heroku login
    Enter your Heroku credentials.
    Email:            adam@example.com
    Password (typing will be hidden):
    Authentication successful.

```
*把你的 SSH 公钥上传到 Heroku，这一点很重要,上传后才能使用 git push 命令。正常情况下,login 命令会自动创建并上传 SSH 公钥。*

## 上传应用
>在工程的根目录下新建一个 **Procfile** 文件，添加如下内容：

```
web: node app.js
```

- 到应用面板页勾选 **web node app.js** ，然后点击 **Apply Changes** 启动应用。

```
$ git init
$ git add .
$ git commit -m "init"
$ git remote add heroku git@heroku.com:yourAppName.git
```
>在 push 到 heroku 服务器之前，我们还需要做一个工作。由于我国某些政策的原因，我们需到**~/.ssh/** 目录下，新建一个 **config** 文件，内容如下：

```
cd ~/.ssh/
vi config
```
```
Host heroku.com
User yourName
Hostname 107.21.95.3
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
port 22
```
```
$ git push heroku master
```

## 成功