---
layout: post
title: "部署一个octopress+git的blog"
date: 2012-08-28 18:07
comments: true
categories: 
---
[Octopress](http://octopress.org)是一个发布静态blog的神器，配合Git pages使用，简直就是天衣无缝，再加上天然支持Markdown编写格式，就更如虎添翼。  
你目前看到的这个blog，就是用[Octopress](http://octopress.org)+[Git pages](http://pages.github.com/) +[disqus](http://disqus.com/)实现的，记录一下大概的步骤：  
**1. 建立github repo**  
 在[github](http://github.com)上建立一个名字为username.github.com的repo，在项目的Admin菜单中，点击Automatic Page Generator按钮进行配置和发布，稍微等一会儿，就可以访问http://username.github.com这个地址，看到你的blog了  
 **2. 配置Octopress环境**  
 这个部分在[Octopress](http://octopress.org)上有比较详细的介绍，我目前的操作系统是Mac OSX 10.8.1，安装了最新版本的ruby 1.3.9p194，基本的步骤如下，首先clone到本地  
 {% codeblock %}
 git clone git://github.com/imathis/octopress.git octopress
 {% endcodeblock %}
 然后，安装依赖的各种工具  
 {% codeblock %}
 gem install bundler  
 rbenv rehash 
 bundle install  
 rake install
 {% endcodeblock %}
 **3. 申请disqus**  
 很简单，去[disqus](http://www.disqus.com)注册一个帐号，记住自己定义的short name就OK了  
 **4. 编辑配置文件**  
 编辑octopress目录下的\_config.yml文件，修改里面的url,title,subtitle,author，以及disqus相关的配置项   
 **5. 写博客**  
 在octopress目录下，执行下面的命令：  
 {% codeblock %}
 rake new_post['new post title']
 {% endcodeblock %}
 系统会自动帮你生成一个markdown后缀的文件，使用你最喜欢的编辑器打开它，就可以开始写你的blog了。  
 **6. 发布**   
 首先执行：  
 {% codeblock %}
 rake generate
 {% endcodeblock %}
 再执行：  
 {% codeblock %}
 rake deploy
 {% endcodeblock %}
 这个时候会要你填写你在[github](http://github.com)上的用户名以及密码，你也可以到_dploy目录下，编辑.git/config文件中的origin字段，直接修改你的地址。  
 
 如果之前的步骤都没有出错的话，访问之前申请的地址，应该可以看到你的blog了，是不是很geek的过程？  
 我在配置安装的过程中，遇到了各种莫名其妙的错误，都通过google一一解决了。  
 另外，你还可以使用各种theme，plugins，以及使用自己的域名等等，慢慢摸索吧。
 
 
