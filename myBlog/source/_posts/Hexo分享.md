---
title: Hexo分享
date: 2019-11-22 21:55:44
tags:
---
# Hexo简介及使用
## 前言
其实之前自己没有写过blog，之后想要把自己沉淀的一些东西记下来，所以就想着搭建一个个人博客网站，目前[hexo](https://hexo.io/zh-cn/ "hexo")被广泛使用，而且社区里有很多主题可以选择，所以就选它了！本篇主要包含以下内容：
1. Hexo简介
2. Hexo安装
3. 简单使用
4. 部署到github

## Hexo简介
#### 什么是Hexo?
Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
#### Hexo的优势
- 快速上手 - 用node安装使用Hexo
- 部署简单，可一键部署
- 强大的主题和插件体系

## Hexo安装
#### 安装前提
- [Node.js](https://nodejs.org/en/ "Node.js")(Node.js 版本需不低于 8.6，建议使用 Node.js 10.0 及以上版本)
- [Git](https://git-scm.com/ "Git")

#### 安装Hexo
安装命令

`$ npm install hexo`

使用hexo命令

`$ npx hexo <command>`

#### 简单使用
新建文件夹

    $ hexo init <folder>
    $ cd <folder>
    $ npm install

新建一篇文章

`$ hexo new [layout] title`

生成静态文件

    $ hexo clean
	$ hexo generate

启动服务器

`$ hexo server`

#### 部署到github
安装插件 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git "hexo-deployer-git")

`npm install hexo-deployer-git --save`

修改_config.yml 中的配置

    deploy：
    	type: git
    	repo: https://github.com/yourName/yourName.github.io
    	branch: 'master'

执行命令 `hexo deploy` 将静态页面推到github

#### 个性化修改

