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

### 添加多说功能
先注册多说，然后获取代码，这个去多说官网看看就知道了。
我使用的是NexT主题，所以就说一下NexT主题的配置
#### 编辑_config.xml，在底部添加
``` bash
duoshuo_shortname: your_duoshuo_shortname
```
#### 编辑themes/next/layout_partials/comments.swig文件，在
``` bash
{% if (theme.duoshuo and theme.duoshuo.shortname) or theme.duoshuo_shortname %}
      <div class="ds-thread" data-thread-key="{{ page.path }}"
           data-title="{{ page.title }}" data-url="{{ page.permalink }}">
      </div>
```
后面添加你自己的多说脚本代码即可：
``` bash
<!-- 多说评论框 end -->
<!-- 多说公共JS代码 start (一个网页只需插入一次) -->
<script type="text/javascript">
var duoshuoQuery = {short_name:"your_duoshuo_shortname"};
(function() {
  var ds = document.createElement('script');
  ds.type = 'text/javascript';ds.async = true;
  ds.src = (document.location.protocol == 'https:' ? 'https:' : 'http:') + '//static.duoshuo.com/embed.js';
  ds.charset = 'UTF-8';
  (document.getElementsByTagName('head')[0] 
   || document.getElementsByTagName('body')[0]).appendChild(ds);
})();
</script>
<!-- 多说公共JS代码 end -->
```
注意代码中的duoshuoQuery和我这里贴的不一样
