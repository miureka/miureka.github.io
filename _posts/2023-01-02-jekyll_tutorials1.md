---
layout: post
title: Jekyll搭建笔记
date: 2023-01-02 
tags: jekyll, reference
---

新年新气象，当了这么多年程序员，终于心血来潮花了几个小时琢磨出来第一个blog。第一篇博客，就总结一下搭建过程纪念一下吧～

TL；DR： 本着极简主义的原则，博客目前部署在github pages上。跟着github官方文档发现了推荐的Jekyll 主题，又顺藤摸瓜找到了几个风格比较喜欢的博客借鉴乐一下。总耗时大概4小时？所以大部分笔记都是集众家之长的复制粘贴。感谢社群的智慧！

### 介绍

 > Jekyll 的核心其实是一个文本转换引擎。它的概念其实就是： 你用你最喜欢的标记语言来写文章，可以是 Markdown，也可以是 Textile,或者就是简单的 HTML, 然后 Jekyll 就会帮你套入一个或一系列的布局中。在整个过程中你可以设置URL路径, 你的文本在布局中的显示样式等等。这些都可以通过纯文本编辑来实现，最终生成的静态页面就是你的成品了。

 一个基本的 Jekyll 网站的目录结构一般是像这样的：

```
.
├── _config.yml
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   ├── post.html
|   └── page.html
├── _posts
|   └── 2016-10-08-welcome-to-jekyll.markdown
├── _sass
|   ├── _base.scss
|   ├── _layout.scss
|   └── _syntax-highlighting.scss
├── about.md
├── css
|   └── main.scss
├── feed.xml
└── index.html
```

这些目录结构以及具体的作用可以参考 [官网文档](http://jekyll.com.cn/docs/structure/) 

进入 _config.yml 里面，修改成你想看到的信息，重新 jekyll server ，刷新浏览器就可以看到你刚刚修改的信息了。



### 本地搭建过程

使用 Jekyll 搭建博客之前要确认下本机环境，Git 环境（用于部署到远端）、[Ruby](http://www.ruby-lang.org/en/downloads/) 环境（Jekyll 是基于 Ruby 开发的）、包管理器 [RubyGems](http://rubygems.org/pages/download) 。Mac 用户需要安装 Xcode 和 Command-Line Tools。
　　
1. (Prerequisite) Install CLI Tools and RubyEnv on Mac 
```zsh
## 根据本机环境调整，google “setup jekyll in XXX”
## 以下配置是M1处理器 + Zsh Terminal
brew install rbenv ruby-build
rbenv install 3.0.0
rbenv global 3.0.0
ruby -v
rbenv rehash
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
echo 'export PATH="/usr/opt/ruby/bin:/usr/lib/ruby/gems/2.6.0/bin:$PATH"' >> ~/.zshrc
```

2. Install Jekall
```
gem install --user-install bundler jekyll
```

3. checkout fav theme
```
git clone https://github.com/leopardpan/leopardpan.github.io.git myblog
```

4. start server
```
bundle exec jekyll serve
```

提示

```
...
  Server address: http://127.0.0.1:4000/
  Server running... press ctrl-c to stop.

```

表示本地服务部署成功。

在浏览器输入 [127.0.0.1:4000](127.0.0.1:4000) ， 就可以看到效果了。



### 放上Github Pages

1. 创建 github.io repositoty （参考任何 github pages教程）
2. 更改本地repo origin (参考 https://stackoverflow.com/a/13716732) 

  ```
  git remote add origin <your_ssh_remote_url>
  git push --set-upstream origin main
  ```

> 注：SSH url 格式: `git@<repo_url>:<url>/<git_repository>.git` 

>  如有需要，先setup Github SSH key，用来和远程repo对话：
- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account


确认github上显示Push 成功后，访问https://miureka.github.io/ - Hello World！



