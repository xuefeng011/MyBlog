---
title: 学习hexo
date: 2016-09-27 23:47:56
tags:
---
什么是Hexo

Hexo 是一个简单地、轻量地、基于Node的一个静态博客框架，可以方便的生成静态网页托管在github和Heroku上，引用Hexo作者 @tommy351 的话：

快速、简单且功能强大的 Node.js 博客框架。A fast, simple & powerful blog framework, powered by Node.js.

GitHub Pages是什么？

GitHub Pages 可以被认为是用户编写的、托管在github上的静态网页。由于它的空间免费稳定， 可以用于介绍托管在github上的Project或者搭建网站。有两种形式: Project Site 和 User/Org Site，二者之间的差异可以戳 GitHub Pages 。基于 GP 创建Site是很方便的，这有一个简单的教程： 学习 Github Page 教你分分钟搭建自己的博客

gp 生成的网站的默认域名是 username.github.io 或者 username.github.io/project-name ，但gp是支持自定义域名的： Custom Domain Name 。购买域名之后，可以和默认的二级域名进行绑定，教程参考： 购买域名、设置DNS

更多关于gp的信息，可以戳： Github Pages Help

Hexo 的安装

由于 Hexo 是基于 Node ，安装前要先安装 Node。我的系统环境：


安装Hexo，要用全局安装，加-g参数。:

npm install -g hexo
查看版本：


查看命令帮助：


1、 help ： 查看帮助信息

2、 init [文件夹名] ： 创建一个hexo项目，不指定文件夹名，则在当前目录创建

3、 version ： 查看hexo的版本

4、 --config config-path ：指定配置文件，代替默认的_config.yml

5、 --cwd cwd-path ：自定义当前工作目录

5、 --debug ：调试模式，输出所有日志信息

6、 --safe ：安全模式，禁用所有的插件和脚本

7、 --silent ：无日志输出模式

安装好后，我们就可以使用Hexo创建项目了。


按照提示，切换到hexo-demo目录，运行 npm install 安装依赖，并启动Hexo服务器：

hexo server
//the same as
//hexo s

这时端口4000被打开了，我们能过浏览器打开地址， http://localhost:4000/ 或者 http://0.0.0.0:4000 。


Hexo的默认界面，Hexo2.4+后采用的默认主题是 Landscape

Hexo的配置

目录和文件


1、 scaffolds ：模板文件夹，新建文章时，Hexo 会根据 scaffold 来建立文件。Hexo 有三种默认布局： post 、 page 和 draft ，它们分别对应不同的路径。新建文件的默认布局是 post ，可以在配置文件中更改布局。用 draft 布局生成的文件会被保存到 source/_drafts 文件夹。

2、 source ：资源文件夹是存放用户资源的地方。

3、 source/_post ：文件箱。（低版本的hexo还会存在一个 _draft ，这是草稿箱）除 _posts 文件夹之外，开头命名为 _ (下划线)的文件/ 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去

4、 themes ：主题 文件夹。Hexo 会根据主题来生成静态页面。

5、 themes/landscape ：默认的皮肤文件夹

6、 _config.yml ：全局的配置文件，每次更改要重启服务。

低版本的Hexo还会生成scripts文件夹，里面用于保存扩展Hexo的脚本文件。

全局配置

可以在 _config.yml 中修改：

# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/
# Site 站点配置
title: Hexo-demo #网站标题
subtitle: hexo is simple and easy to study #网站副标题
description: this is hexo-demo #网栈描述
author: pomy #你的名字
language: zh-CN #网站使用的语言
timezone: Asia/Shanghai #网站时区
# URL #可以不用配置
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://yoursite.com #网址，搜索时会在搜索引擎中显示
root: / #网站根目录
permalink: :year/:month/:day/:title/ #永久链接格式
permalink_defaults: #永久链接中各部分的默认值
# Directory 目录配置
source_dir: source #资源文件夹，这个文件夹用来存放内容
public_dir: public #公共文件夹，这个文件夹用于存放生成的站点文件
tag_dir: tags #标签文件夹
archive_dir: archives #归档文件夹
category_dir: categories #分类文件夹
code_dir: downloads/code #Include code 文件夹
i18n_dir: :lang #国际化文件夹
skip_render: #跳过指定文件的渲染，您可使用 glob 来配置路径
# Writing 写作配置
new_post_name: :title.md # 新文章的文件名称
default_layout: post #默认布局
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0 #把文件名称转换为 (1) 小写或 (2) 大写
render_drafts: false #显示草稿
post_asset_folder: false #是否启动资源文件夹
relative_link: false #把链接改为与根目录的相对位址
future: true
highlight: #代码块的设置
enable: true
line_number: true
auto_detect: true
tab_replace:
# Category & Tag 分类 & 标签
default_category: uncategorized #默认分类
category_map: #分类别名
tag_map: #标签别名
# Date / Time format 时间和日期
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
# Pagination 分页
## Set per_page to 0 to disable pagination
per_page: 10 #每页显示的文章量 (0 = 关闭分页功能)
pagination_dir: page #分页目录
# Extensions 扩展
## Plugins: http://hexo.io/plugins/ 插件
## Themes: http://hexo.io/themes/ 主题
theme: landscape #当前主题名称
# Deployment #部署到github
## Docs: http://hexo.io/docs/deployment.html
deploy:
type:
一般主题下有一个 languages 文件夹，用于对应 language 配置项。比如在 ejs 中有：

<%= __('tags') %>
language 的配置项是 zh-CN ，则会在 languages 文件夹下找到 zh-CN.yml 文件中对应的项来解释。

修改全局配置时，注意缩进，同时注意冒号后面要有一个空格。

主题配置

主题的配置文件在 /themes/主题文件夹/_config.yml ，一般包括导航配置(menu)，内容配置(content)，评论插件，图片效果(fancybox)和边栏(sidebar)。

Hexo提高了大量的主题，可以在全局配置文件中更改主题：

# Extensions 扩展
## Plugins: http://hexo.io/plugins/ 插件
## Themes: http://hexo.io/themes/ 主题
theme: 你的主题名称
主题的文件目录必须在 themes 目录下。 Hexo主题更换教程

更多Hexo主题戳此： Hexo Themes 。

基本使用

写文章通过 new 命令新建一篇文章：

$ hexo new [layout] <title>
//same as
hexo n
其中layout是可选参数，默认值为 post 。


如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，需用引号括起来。

Hexo提供的layout在 scaffolds 目录下，也可以在此目录下自建layout文件。新建的文件则会保存到 source/_post 目录下。



然后启动服务器，便能看到刚刚发表的文章


发表的文章会全部显示，如果文章很长，就只要显示文章的摘要就行了。在需要显示摘要的地方添加如下代码即可：

以上是摘要
<!--more-->
以下是余下全文

刷新，就能够看到只显示摘要了，同时会提供 Read More 的链接：


这个文字可以更改，在主题的配置文件( themes/主题文件夹/_config.yml )中，找到 Content ：

# Content
excerpt_link: Read More #可以更改成想要显示的文字
fancybox: true
此外，可以修改文章的参数，打开 scaffolds/post.md ，增加类别和描述：


再新建一篇文章，就能看到增加了文章参数：


tags 和 categories 有多个，则用数组形式。

部署在部署之前，需要通过命令把所有的文章都做静态化处理，就是生成对应的html, javascript, css，使得所有的文章都是由静态文件组成的：

hexo generate
//same as
hexo g

在本地目录下，会生成一个public的目录，里面包括了所有静态化的文件。

生成静态文件之后，如果要发布到github，还需要配置 deploy 指令。在全局的配置文件中找到 deploy ：

# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
type: git
repo: https://github.com/dwqs/dwqs.github.io.git
branch: master
然后还要安装 hexo-deployer-git ：

npm install hexo-deployer-git -S
最后利用hexo指令发布到github：

hexo d
//same as
hexo deploy

在github上便能看到刚刚部署的静态web网站：


如果部署的是个人页，新建的仓库必须的 your-user-name.github.io 。

总结

Hexo常用命令：

hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
文章使用的repo： https://github.com/dwqs/dwqs.github.io.git

访问地址： https://dwqs.github.io/

使用的主题： https://github.com/dwqs/nx