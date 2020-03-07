# Fly's Blog

### 一、安装Git、Node.js以及Hexo
> Hexo 官方文档：https://hexo.io/zh-cn/docs/

### 二、搭建博客
1. 初始化：hexo init
2. 按照package.json安装所需要的组件放在生成的node_modules文件夹中：npm install
3. 配置博客信息
    ```java
    # Site
    title: Fly's Blog
    subtitle: 'Only if you asked to see me, our meeting would be meaningful to me'
    description: '心情，日记，随笔，读后感'
    keywords:
    author: Hao Liu
    language: zh-CN
    timezone: ''

    									......

    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    url: https://fly-liuhao.github.io/

    									......
    
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
      type: git
      repo: git@github.com:fly-liuhao/fly-liuhao.github.io.git
      branch: master
    ```

### 三、部署/发布到github

1. 创建github仓库:
    仓库名格式：`girhub名称` + `.github.io`，eg：Hins.github.io

2. 安装 hexo-deployer-git
    $ npm install hexo-deployer-git --save

3. 修改`_config.yml`，修改博客地址以及博客的远程仓库链接
    ```java 
    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    url: https://fly-liuhao.github.io/
    
    									......
    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
      type: git
      repo: git@github.com:fly-liuhao/fly-liuhao.github.io.git
      branch: master
    ```
### 四、将源代码提交到github
1. 在跟目录初始化git仓库：`git init`
2. 将原文件添加到本地仓库
3. 设置远程仓库地址：`git remote add origin git@github.com:fly-liuhao/fly-liuhao.github.io.git`
	注意：如果使用的https链接的需先断开与远程仓库的连接：`git remote rm origin `
4. 创建源文件分支：`git branch source`，并切换分支：`git checkout source`
5. 推送到远程仓库`git push --set-upstream origin source`

### 四、更换主题
1. 在你的博客根目录里下载主题：`git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly`
2. 应用主题，修改站点配置文件_config.yml，把主题改为Butterfly：`theme: Butterfly`
3. 如果你没有 pug 以及 stylus 的渲染器，请下载安装：`npm install hexo-renderer-pug hexo-renderer-stylus --save or yarn add hexo-renderer-pug hexo-renderer-stylus`
4. 安装cheerio（升级到hexo 4.2.0 ，会出现报错：Error: Cannot find module ‘cheerio’）：`npm install cheerio --save`

### 五、主题配置
> 我所下载的主题文档：https://jerryc.me/posts/21cfbf15/
1. 更改主题语言为`简体中文`
	- 打开主题中的`[languages]`文件夹，查看主题中支持的语言：default、en、zh-CN、zh-TW
	- 修改博客的配置文件`_config.yml`：`language: zh-CN`	
	
2. 主题配置文件平滑升级
	- 为了主题的平滑升级, Butterfly 使用了 data files特性。
	- 推荐把主题默认的配置文件_config.yml复製到 Hexo 工作目录下的source/_data/butterfly.yml，如果source/_data的目录不存在那就创建一个。
    > 注意，如果你创建了butterfly.yml, 它将会替换主题默认配置文件_config.yml里的配置项 (不是合并而是替换), 之后你就只需要通过git pull的方式就可以平滑地升级 theme-butterfly了。
	
3. 将主题的配置文件`butterfly.yml`中的繁体字转化为简体中文
	
	- 在线繁体-简体转换网站：https://www.aies.cn/
	
4. 配置文章发布模板
   - Page
       ```java
        ---
        title: {{ title }}
        date: {{ date }}
        type: （tags,link,categories这三个页面需要配置）
        comments: (是否需要显示评论，默认true)
        description:
        top_img: (设置顶部图)
        mathjax:
        katex:
        ---
       ```
   - Post
        ```java
        ---
        title: {{ title }}
        date: {{ date }}
        tags:
        categories:
        keywords:
        description:
        top_img: （除非特定需要，可以不写）
        comments  是否显示评论（除非设置false,可以不写）
        cover:  缩略图
        toc:  是否显示toc （除非特定文章设置，可以不写）
        toc_number: 是否显示toc数字 （除非特定文章设置，可以不写）
        copyright: 是否显示版权 （除非特定文章设置，可以不写）
        mathjax:
        katex:
        hide: （是否想要隐藏文章）
        ---
       ```

5. 添加页面
	- 标签页：
        输入`hexo new page tags`
        修改`source/tags/index.md`文件如下：
        
        ```java
	     ---
        title: 标籤
        date: 2018-01-05 00:00:00
        type: "tags"
        ---
        ```
   - 分类页：
      输入`hexo new page categories`
      修改`source/categories/index.md`文件如下：
      ```java
      ---
      title: 分类
      date: 2018-01-05 00:00:00
      type: "categories"
      ---
      ```
      
   - 友情链接：
     输入 `hexo new page link`
     修改`source/link/index.md`文件如下：
     
     ```java
     ---
     title: 友情链接
     date: 2018-06-07 22:17:49
     type: "link"
     ---
     ```
     在Hexo博客目录中的`source/_data`，创建一个文件`link.yml`
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
        class_name: 链接无效
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
     友情链接界面设置（在友情链接上写上自己的个人资料，方便其他人添加），在`Butterfly.yml`配置：
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

6. 音乐页面
	> 参考hexo-tag-aplayer链接：https://github.com/MoePlayer/hexo-tag-aplayer
	> 使用教程链接1：https://blog.csdn.net/hushhw/article/details/88092728
	> 使用教程链接2：https://www.jianshu.com/p/f1005ae09e5a
	- 安装插件：npm install --save hexo-tag-aplayer
	- 在配置文件 `_config.yml`中添加：
        ```java
        # 音乐播放插件
        aplayer:
          meting: true
        ```
   - 创建music目录：`hexo new page music`
   - 网易云链接：https://music.163.com/
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
           	 
           	# 聆听这个世界
           	{% meting "551340498" "netease" "song" "theme:#555" "mutex:true" "listmaxheight:340px" "preload:auto" %}
           	---
           	# OH MY GIRL
           	{% meting "3175659640" "netease" "playlist" "theme:#555" "volume:0.5" "mutex:true" "listmaxheight:340px" "preload:auto" %}
     ```

7. 电影页面
	> 参考链接：https://github.com/mythsman/hexo-douban
	- 安装插件：`npm install hexo-douban --save`
	- 在配置文件 `_config.yml`中添加：
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
	- 豆瓣链接：https://www.douban.com/
	- 生成指定页面：`hexo douban -bm`
		> 1. 需要注意的是，通常大家都喜欢用`hexo d`来作为`hexo deploy`命令的简化，但是当安装了`hexo douban`之后，就不能用`hexo d`了，因为`hexo douban`跟`hexo deploy`的前缀都是`hexo d`
		>
		> 2.  如果builtin属性设置为：true，则每次不需要执行该命令，直接使用`hexo g`生成页面即可

8. 关于页面

### 七、主题优化
#### （一）开启评论功能
1. 使用 Laibili（来必力）
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

2. 使用 Valine（免费）
	- 注册LeanCloud（需完成邮箱认证以及）
	- 并创建一个开发版应用
	- 在LeanCloud -> 存储 -> 创建Class -> 无限制的Class（坑点1）
	- 在LeanCloud-设置-把除数据存储其他选项都关闭。
class名称为：Comment

#### （二）使用PWA实现Web应用
1. 关于PWA应用
	
	- https://www.ithome.com/0/414/429.htm
2. 使用PWA渐进式框架的网站
	> 实例博客1：https://diygod.me/
	> 实例博客2：https://wangyaxing.cn/
	> 微博：https://m.weibo.cn/
	> 推特：http://mobile.twitter.com/
	> IT之家：https://m.ithome.com/
3. 使用文档
	- hexo-theme-melody：https://molunerfinn.com/hexo-theme-melody-doc/zh-Hans/additional-package-support.html#pwa
	
	- hexo-theme-butterfly：https://jerryc.me/posts/21cfbf15/#PWA
	
	- 配置注意事项：
	
	  > 1. manifest.json创建的位置是主题中的source文件夹
	  > 2. 因为manifest.json中使用到各尺寸Logo图片，根据路径在主题中的source中建立相应的文件夹，放入指定尺寸大小以及名称的Logo图片
	  > 3. 图片尺寸一定要符合要求必须是长宽像素值大小相等，要不应用的Logo图片无法加载显示
3. 使用到的工具
	- Png改变大小：https://www.iloveimg.com/zh-cn/resize-image
	- Png-svg：http://www.bejson.com/convert/image_to_svg/

#### （三、）添加本地搜索
1. 官方github链接：https://github.com/wzpan/hexo-generator-search
2. 使用教程
	- 安装：`npm install hexo-generator-search --save`

#### （四）添加字数统计功能
2. 使用：
	- 安装：`npm install hexo-wordcount --save`
### 七、编写文章
1. 使用next主题编写文章（注意，书写不是markdown规範，而是hexo特有的功能，移植于next主题，故在其它地方会显示不出效果）
	> 链接：https://theme-next.org/docs/tag-plugins/note
	
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
	
3. 占位，占位，占位，占位，占位，
