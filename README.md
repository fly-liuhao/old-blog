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

### 三、提交到github