---
title: 手把手教你快速搭建个人博客 Hexo + Github
top_img: http://lilibei.net/background/b18.jpg
comments: true
toc: true
toc_number: true
copyright: true
hide: false
date: 2020-03-03 13:07:54
categories: 技术
tags:
	- Hexo
	- GitHub Pages
keywords: Hexo
description: 利用Hexo + GitHub Pages快速搭建自己的个人博客
cover: http://lilibei.net/background/b18.jpg
---


> 平时学习查找资料发现了很多个人博客，搭建的很不错，一直想抽空自己也动手实践一下，正好趁着新型冠状肺炎这段宅在家的空，赶紧搭建一下自己个人博客
>  - 先来预览一下博主的个人博客：[Fly's Blog](https://fly-liuhao.github.io/)
>  - 动手能力差的同学可以先跟着B站小匠的视频快速搭建一下，之后再参考这篇博文进行博客的其他设置：[B站搭建博客教程传送门](https://www.bilibili.com/video/av55851824?from=search&seid=10776387286422523572)

@[TOC](目录)
### 一、安装Git、Node.js以及Hexo
- Hexo 官方文档：https://hexo.io/zh-cn/docs/
- 这里不是重点，不赘述，具体参考Hexo的官方文档

### 二、搭建博客
####  1. 初始化一个博客
- `hexo init` 或者 `hexo init + 文件夹名称`
#### 2. 安装博客所需组件
- 进入到博客所在目录中，将 package.json 所需要的组件进行安装（会自动安装到目录中生成的node_modules文件夹下）：`npm install`
#### 3. 修改博客的基础配置信息
- 打开目录下的 _config.yml 文件，修改如下信息
    ```java
    # Site
    // 博客的名称
    title: Fly's Blog
    // 博客副标题，可以作为你的个签
    subtitle: 'Only if you asked to see me, our meeting would be meaningful to me'
    // 博客的描述（博客的用途）
    description: '心情，日记，随笔，读后感'
    // 博客的关键词。使用 , 分隔多个关键词。
    keywords: java, html, css, jQuery
    // 博客的作者
    author: Hao Liu
    // 语言设置，不同主题语言形式不一样，具体参考使用主题文件夹下的languages文件夹
    language: zh-CN
    // 时区设置，默认是系统的使用的时区，大陆可以填写 Asia/Shanghai
    timezone: 'Asia/Shanghai'
    ```
#### 4. 创建本地服务启动博客进行预览
- 打开博客根目录下打开 Git Bash，依次输入一下指令
	- 清除缓存文件 (db.json) 和已生成的静态文件 (public)：`hexo clean`
	   一般再执行 `hexo generate` 前执行此命令，防止修改内容失效
	- 生成静态文件：`hexo generate`
	- 启动服务器：`hexo server`
	默认情况下，访问网址为： http://localhost:4000/
- 打开浏览器，访问 http://localhost:4000/
  正常情况下即可查看到你的博客内容如下：
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200302212948756.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0ZseV8xMjEz,size_16,color_FFFFFF,t_70)
### 三、部署 / 发布到github
#### 1. 创建github仓库:
- 仓库名格式：`github用户名` + `.github.io`
  eg：Hins.github.io

#### 2. 安装 hexo-deployer-git
- 用于提交本地生成的页面内容到 github 仓库
- 命令： `npm install hexo-deployer-git --save`

#### 3. 再次修改 `_config.yml` 文件
- 修改博客地址以及博客的远程仓库链接
    ```java 
    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    // 此处博主使用的是 Github Page 做个人博客的 Websites
    url: https://fly-liuhao.github.io/
    
    									......
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    // 此处填写你的 github 仓库，可以使用 http 或者 SSH(推荐使用)，分支必须为主分支 master
    deploy:
      type: git
      repo: git@github.com:fly-liuhao/fly-liuhao.github.io.git
      branch: master
    ```
### 四、将Blog源代码提交到github
#### 1. 在根目录初始化本地仓库
- 初始化一个本地仓库：`git init`
#### 2. 将原文件添加到本地仓库
- 将本地文件放到暂存区：`git add .`
- 将暂存区的文件提交到本地仓库：`git commit -m '你的提交描述内容'`
#### 3. 将本地仓库 push 到远程 gitHub 仓库中
- 设置远程仓库地址：`git remote add origin git@github.com:fly-liuhao/fly-liuhao.github.io.git`
	注意：如果需要改变与远程仓库的链接方式，需先断开与远程仓库的连接：`git remote rm origin `
- 创建源文件分支：`git branch source`，并切换到该分支：`git checkout source`
- 推送到远程仓库：`git push --set-upstream origin source`

### 五、更换Blog主题
#### 1. 在你的博客根目录里下载主题
- Hexo 主题参考链接：[https://hexo.io/themes/](https://hexo.io/themes/)
- 选择你喜欢的一个主题进行下载，博主这里选择的是 `Butterfly` 主题：`git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly`
	下载完成即可在 themes 文件夹下看到下载的主题文件夹：
	![在这里插入图片描述](https://img-blog.csdnimg.cn/20200302215219971.png)
#### 2. 应用主题
- 修改站点配置文件_config.yml，把主题改为Butterfly：`theme: Butterfly`
#### 3. 安装 pug 以及 stylus 的渲染器
- 如果你没有 pug 以及 stylus 的渲染器，请下载安装：`npm install hexo-renderer-pug hexo-renderer-stylus --save or yarn add hexo-renderer-pug hexo-renderer-stylus`
#### 4. 安装cheerio
- hexo 4.2.0版本之后 ，会出现报错 “Error: Cannot find module ‘cheerio’” 因此需要安装 cheerio：`npm install cheerio --save`

### 六、主题的基础配置
> 注意：不同主题配置是不一样的，这里博主以选择的 Butterfly 主题进行配置，如有小伙伴选择的是其他主题，请参考主题的官方文档进行配置（主题 github 中的 README 中一般有给具体配置的参考文档）
> - 博主使用的 Butterfly 主题配置参考文档：[https://jerryc.me/posts/21cfbf15/](https://jerryc.me/posts/21cfbf15/)
> （注意：如果链接进不去，选择高级，继续访问即可）
> - 这里其实你完全可以跟着文档配置自己的博客，下面是博主自己配置的，仅供参考（如有细节不到位的请参考文档）
#### 1. 更改主题语言为`简体中文`
- 打开主题中的`[languages]`文件夹，查看主题中支持的语言：default、en、zh-CN、zh-TW
- 修改博客的配置文件`_config.yml`：`language: zh-CN`	
	
#### 2. 主题配置文件平滑升级
- 为了主题的平滑升级, Butterfly 使用了 data files 特性。
- 推荐把主题默认的配置文件 _config.yml 复製到 Hexo 工作目录下的source/_data/butterfly.yml，如果source/_data的目录不存在那就创建一个。
  > 注意，如果你创建了butterfly.yml, 它将会替换主题默认配置文件_config.yml里的配置项 (不是合并而是替换), 之后你就只需要通过git pull的方式就可以平滑地升级 theme-butterfly了。

#### 3. 将主题的配置文件`butterfly.yml`中的繁体字转化为简体中文
- 因为作者好像是台湾人，配置中的注释全是繁体，如有介意可以使用下面简繁转化的网站进行转换：Ctrl + A、Ctrl + C、Ctrl + V ...
- 在线繁体-简体转换网站：[https://www.aies.cn/](https://www.aies.cn/)

#### 4. 配置文章发布模板
   - Page（页面）
       ```java
        ---
        title: {{ title }}
        date: {{ date }}
        type: （tags，link，categories 这三个页面需要配置）
        comments: (是否需要显示评论，默认true)
        description:（页面描述）
        top_img: (设置顶部图，链接形式)
        mathjax:（用于一些数学表达式显示配置）
        katex:（用于一些数学表达式显示配置）
        ---
       ```
   - Post（文章）
        ```java
        ---
        title: {{ title }}
        date: {{ date }}
        tags:（文章的标签）
        categories:（文章所属分类）
        keywords:（关键字s）
        description:（描述）
        top_img: （除非特定需要，可以不写）
        comments  （是否显示评论，默认开启，除非设置false,可以不写）
        cover: （缩略图链接）
        toc: （是否显示文章目录，除非特定文章设置，可以不写）
        toc_number: （是否显示目录的数字序号，除非特定文章设置，可以不写）
        copyright: （是否显示版权，默认开启，除非特定文章设置，可以不写）
        mathjax: （用于一些数学表达式显示配置）
        katex:（用于一些数学表达式显示配置）
        hide: （是否想要隐藏文章）
        ---
       ```

#### 5. 添加基本的页面
- 标签页：
	- 输入命令：`hexo new page tags`
	- 修改`source/tags/index.md`文件如下：    
		```java
		---
		title: 标籤
		date: 2020-03-21 00:00:00
		type: "tags"
		---
		```
- 分类页：
	- 输入命令：`hexo new page categories`
	- 修改`source/categories/index.md`文件如下：
		```java
		---
		title: 分类
		date: 2020-03-21 00:00:00
		type: "categories"
		---
		```
- 友情链接：
	- 输入命令： `hexo new page link`
	- 修改`source/link/index.md`文件如下：
		```java
		---
		title: 友情链接
		date: 2020-03-21 00:00:00
		type: "link"
		---
		```
	- 在Hexo博客目录中的`source/_data`，创建一个文件`link.yml`
		```java
		class:
		  class_name: 友情链接
		  link_list:
		    1:
		      name: xxx
		      link: https://blog.xxx.com
		      avatar: https://cdn.xxxxx.top/avatar.png
		      descr: xxxxxxx
		    2:
		      name: xxxxxx
		      link: https://www.xxxxxxcn/
		      avatar: https://xxxxx/avatar.png
		      descr: xxxxxxx  
		
		class2:
		  class_name: 无效链接
		  link_list:
		    1:
		     name: 梦xxx
		     link: https://blog.xxx.com
		     avatar: https://xxxx/avatar.png
		     descr: xxxx
		   2:
		     name: xx
		     link: https://www.axxxx.cn/
		     avatar: https://x
		     descr: xx
		```
	- 友情链接界面设置（在友情链接上写上自己的个人资料，方便其他人添加），在`Butterfly.yml`配置：
	    ```java
	    Flink:
	      headline: 友情链接
	      info_headline: 我的Blog资料
	      name: Blog 名字： JerryC
	      address: Blog 地址： https://jerryc.me/
	      avatar: Blog 头像： https://jerryc.me/img/avatar.png
	      info: Blog 简介： 今日事,今日毕
	      comment: 如果需要交换友链,请留言
	    ```
- 关于页面
	- 输入命令：`hexo new page about`
     - 修改`source/about/index.md`文件
     	> 这里自我发挥，博主这里放的是本人的个人简历（可以帮助找工作哦），你也可以写一些你的自我介绍，具体参考其他人的个人博客设计
#### 6. 音乐页面
> 参考hexo-tag-aplayer链接：[https://github.com/MoePlayer/hexo-tag-aplayer](https://github.com/MoePlayer/hexo-tag-aplayer)
> - 使用教程链接1：[https://blog.csdn.net/hushhw/article/details/88092728](https://blog.csdn.net/hushhw/article/details/88092728)
> - 使用教程链接2：[https://www.jianshu.com/p/f1005ae09e5a](https://www.jianshu.com/p/f1005ae09e5a)
- 安装插件：npm install --save hexo-tag-aplayer
- 修改配置，在配置文件 `_config.yml`中添加：
	 ```java
	 # 音乐播放插件
	 aplayer:
	   meting: true
	 ```
- 创建music目录：`hexo new page music`
- 网易云链接：[https://music.163.com/](https://music.163.com/)
- 修改`source/music/index.md`文件如下：
	```java
	---
	title: 那些年，听过的音乐
	type: "music"
	comments: true
	top_img: https://cdn.jsdelivr.net/gh/jerryc127/CDN@latest/Photo/music.jpg
	date: 2020-02-19 11:59:50
	description: 轻抚受伤的心灵
	mathjax:
	katex:
	---
	   	 
	# My Love
	// 注意：第一串数字是你网易云歌曲的ID，浏览器地址栏获取（此行为注释，文件中请删掉此行）
	{% meting "551340498" "netease" "song" "theme:#555" "mutex:true" "listmaxheight:340px" "preload:auto" %}
	---
	# 聆听这个世界
	// 注意：第一串数字是你网易云歌单的ID，浏览器地址栏获取（此行为注释，文件中请删掉此行）
	{% meting "3175659640" "netease" "playlist" "theme:#555" "volume:0.5" "mutex:true" "listmaxheight:340px" "preload:auto" %}
	```

#### 7. 书籍、电影页面
> 参考链接：[https://github.com/mythsman/hexo-douban](https://github.com/mythsman/hexo-douban)
> 这里调用的是你豆瓣的接口，只需要提供你的ID，同样也是浏览器地址栏获取（需登录豆瓣）
- 安装插件：`npm install hexo-douban --save`
- 在配置文件  `_config.yml` 中添加：
	```java
	# 书籍、电影插件
	douban:
	  user: 175423653 # 你的豆瓣ID
	  builtin: false # 是否将生成页面的功能嵌入hexo s和hexo g中
	  book:
	    title: '那些年,我看過的書籍'
	    quote: '世界上任何的书籍都不能带给你好运，但是它们能让你悄悄的成为你自己'
	  movie:
	    title: '那些年,我看過的電影'
	    quote: '过去、现在、未来'
	  timeout: 10000
	```
- 豆瓣链接：[https://www.douban.com/](https://www.douban.com/)
- 生成指定页面：`hexo douban -bm`
	- 需要注意的是，通常大家都喜欢用`hexo d`来作为`hexo deploy`命令的简化，但是当安装了`hexo douban`之后，就不能用`hexo d`了，因为`hexo douban`跟`hexo deploy`的前缀都是`hexo d`
	- 果 `builtin` 属性设置为：true，则每次不需要执行该命令，直接使用`hexo g`生成页面即可

### 七、主题的基础配置
#### 1. 开启评论功能
> 推荐使用 Valine ，Laibili加载过于慢，评论是还需跳转登录，可直接使用 Valine 实现评论功能
- 使用 Laibili（来必力）
	- 注册账户并登录：http://livere.com/
	- 点击管理页面，然后根据提示获取用户ID（代码管理中的data-uid后面）
        ```java
        <!-- 来必力City版安装代码 -->
        <div id="lv-container" data-id="city" data-uid="MTAyMC80ODxxxxxyNTIzNQ==">
        							.........
        ```
	- 修改主题配置
		```java
		laibili:
	   enable: true
	   uid: MTAyMC80ODxxxxxyNTIzNQ==
	  ```

- 使用 Valine（推荐使用）
	> 参考教程1：[https://www.jianshu.com/p/728a9594bb6c](https://www.jianshu.com/p/728a9594bb6c)
	> 参考教程2：[https://bluelzy.com/articles/use_valine_for_your_blog.html](https://bluelzy.com/articles/use_valine_for_your_blog.html)
	- 注册LeanCloud（需完成邮箱认证）
	- 创建一个开发版应用
	- 获取 `appId` 以及 `appKey`
	- 修改主题配置 butterfly.yml 如下：
		```java
		# valine comment system. https://valine.js.org
		valine:
		  enable: true # if you want use valine,please set this value is true
		  appId: xxxxxxxxxxxxxxx # 填写你获取的 app id
		  appKey: xxxxxxxxxxxxxxx # 填写你获取的 app key
		  notify: true # valine mail notify (true/false) https://github.com/xCss/Valine/wiki
		  verify: false # valine verify code (true/false)
		  pageSize: 10 # comment list page size
		  avatar: monsterid # gravatar style https://valine.js.org/#/avatar
		  lang: zh-cn # i18n: zh-cn/en
		  placeholder: 说点什么吧... # valine comment input placeholder(like: Please leave your footprints )
		  guest_info: nick,mail,link #valine comment header info
		  bg: /img/comment_bg.png # valine background
		  count: false # top_img显示评论数
		```

#### 2.使用PWA实现Web应用
-  关于PWA应用
	> 直观认识：[https://www.ithome.com/0/414/429.htm](https://www.ithome.com/0/414/429.htm)
- 使用PWA渐进式框架的网站
	> - 实例博客1：[https://diygod.me/](https://diygod.me/)
	> - 实例博客2：[https://wangyaxing.cn/](https://wangyaxing.cn/)
	> - 微博：[https://m.weibo.cn/](https://m.weibo.cn/)
	> - 推特：[http://mobile.twitter.com/](http://mobile.twitter.com/)
	> - IT之家：[https://m.ithome.com/](https://m.ithome.com/)
- 使用文档
	- hexo-theme-melody 主题：[https://molunerfinn.com/hexo-theme-melody-doc/zh-Hans/additional-package-support.html#pwa](https://molunerfinn.com/hexo-theme-melody-doc/zh-Hans/additional-package-support.html#pwa)
	- hexo-theme-butterfly 主题：[https://jerryc.me/posts/21cfbf15/#PWA](https://jerryc.me/posts/21cfbf15/#PWA)
	- 配置注意事项：
	  > - manifest.json创建的位置是主题中的source文件夹
	  > - 因为manifest.json中使用到各尺寸Logo图片，根据路径在主题中的source中建立相应的文件夹，放入指定尺寸大小以及名称的Logo图片
	  > - 图片尺寸一定要符合要求必须是长宽像素值大小相等，要不应用的Logo图片无法加载显示
- 使用到的工具
	- Png改变大小：[https://www.iloveimg.com/zh-cn/resize-image](https://www.iloveimg.com/zh-cn/resize-image)
	- Png-svg：[http://www.bejson.com/convert/image_to_svg/](http://www.bejson.com/convert/image_to_svg/)

#### 3. 添加本地搜索
- 官方github链接：https://github.com/wzpan/hexo-generator-search
- 使用教程
	- 安装：`npm install hexo-generator-search --save`
	- 修改主题配置文件 butterfly.yml 如下：
#### 4. 添加字数统计功能
- 使用：
	- 安装：`npm install hexo-wordcount --save`
	- 修改主题配置文件 butterfly.yml 如下：
### 八、关于创建文章 与 文章发布
1. 使用next主题编写文章（注意，书写不是markdown规範，而是hexo特有的功能，移植于next主题，故在其它地方会显示不出效果）
	> 链接：[https://theme-next.org/docs/tag-plugins/note](https://theme-next.org/docs/tag-plugins/note)
	
	用法：
	```Markdown
	{% note [class] [no-icon] %}
	Any content (support inline tags too.io).
	{% endnote %}
	
	[class]   : default | primary | success | info | warning | danger.
	[no-icon] : Disable icon in note.
	
	All parameters are optional.
	```

2. 使用`Gallery`相册，在文章中插入图片
	> 区别于旧版的Gallery相册,新的Gallery相册会自动根据图片长度进行排版，书写也更加方便，与markdown格式一样。可根据需要插入到相应的md
   
	用法：
	```markdown
	{% gallery %}
	markdown 图片格式
	{% endgallery %}
	
	eg：
	   
	{% gallery %}
	![](https://gratisography.com/wp-content/uploads/2019/10/gratisography-scary-pumpkin-hand-900x600.jpg)
	![](https://gratisography.com/wp-content/uploads/2019/10/gratisography-fresh-fish-dinner-900x600.jpg)
	![](https://gratisography.com/wp-content/uploads/2019/10/gratisography-mountain-cloud-landscape-900x600.jpg)
	![](https://picjumbo.com/wp-content/uploads/iphone-free-stock-photos-2210x3315.jpg)
	![](https://picjumbo.com/wp-content/uploads/young-millennial-girl-drinking-lemonade-and-overlooking-the-city-2210x1473.jpg)
	![](https://picjumbo.com/wp-content/uploads/modern-graphic-designer-essentials_free_stock_photos_picjumbo_HNCK4919-2210x1474.jpg)
	{% endgallery %}
	```
##### <center> <font  color = gray>OK，配置基本可以了，重新部署一下访问即可！ </font></center>
 <center> <font  color = gray>欢迎将你的个人博客链接留言在下方</font></center>
  <center> <font  color = gray>互相交换友链呀~</font></center>
