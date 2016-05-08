---
title: Hexo部署到github流程
---


### 配置deploy
在_config.xml文件中添加如下配置，注意冒号后面要有空格：
``` bash
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: master
```

### 安装hexo-deployer-git包
``` bash
$ npm install hexo-deployer-git --save
```

###  添加ssh key
``` bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

###  部署
``` bash
$ hexo clean
$ hexo generate
$ hexo deploy
```
