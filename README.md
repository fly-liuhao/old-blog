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
4. 安装cheerio（升级到hexo 4.2.0 ，会出现报错：Error: Cannot find module ‘cheerio’）：`npm install cheerio`
