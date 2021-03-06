---
title: 搭建个人博客
tags: 博客
abbrlink: 23941
date: 2018-06-11 00:26:20
---

- OS: Mac 10.13
- framework: Hexo
- blog: Github pages

用Github pages发布blog， 同时在同一个repo新建名叫hexo的branch来管理markdown源文件 

## 一. 在github新建repo

1. 拥有一个 github 账号， 
2. 新建repo叫 `<username>.github.io`, 用你的账号替换`<username>`

<!-- more -->

## 二. 在本地创建hexo project

 建议根据 [**hexo**](https://hexo.io/zh-cn/docs/index.html) 文档进行安装配置

1. 安装 git
```
$ brew install git
```

2. 安装 node.js
从[官网下](https://nodejs.org/en/#download)载安装包

3. 安装 hexo
```
$ npm install -g hexo-cli
```

4. 本地建站
将`<username>`换成自己 Github 的账号
```
$ hexo init <username>.github.io
$ cd <username>.github.io
$ npm install
```

5. 基础配置
打开`<username>.github.io/_config.yml` 
更改以下参数，将`<your_repo_address>` 换成第一步中新建repo的地址
```
title: <your_blog_name>
author: <your_name>
...
deploy: 
    type: git
    repo: <your_repo_address>
    branch: master
```

## 三. 上传源文件

1. 在 `<username>.github.io`中执行
```
$ git init
$ git remote add origin <your_repo_address>
$ git status
$ git add source/_posts _config.yml
$ git checkout -b hexo
$ git commit -m initial
$ git push origin/hexo hexo
```

2. 设置**hexo**为默认分支

## 四. 发表文章
1. 新建文章
```
$ hexo new '新文章'
```

2. 本地测试
```
$ hexo generate
$ hexo server
```
    打开 http://localhost:4000/ 测试

3. 上传Github
```
$ hexo deploy
```

