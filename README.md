Octopress in Docker
==============================

创建Octopress博客docker镜像的Dockerfile[Octopress framework](https://github.com/imathis/octopress)

## 初始化安装

运行实例要保持config和posts持续性, 你必须映射本地目录到Octopress容器:

    docker pull lenciel/docker-octopress
    git clone https://github.com/lenciel/docker-octopress
    cd docker-octopress
    docker run -d -v `pwd`/source:/srv/octopress-master/source -v `pwd`/config:/srv/octopress-master/config -p 80:80 lenciel/docker-octopress


## 使用

新建文章的两种方式:

### 自动

运行一个交互的shell:

    docker run -v `pwd`/source:/srv/octopress-master/source -v `pwd`/config:/srv/octopress-master/config -p 80:80 -i -t --entrypoint="/bin/bash" dockerxman/docker-octopress

    rake new_post["Post title"]

然后在`source/_posts/`目录里面编辑它。　

当你新建了一个博客, 它可以通过Octopress容器在后台模式重新运行。

### 手动

在 `source/_posts` 目录里面创建 `YYYY-MM-DD-title.markdown` 文件:
    
    ---
    layout: post #当前使用的模板文件source/_layout。
    title: "Post Title" #title：文章标题。当前显示的是生成文件时帮助生成路径的名称，这里可以任意修改。例如，这里可以改为“文章标题”。
    date: YYYY-MM-DD HH:MM #文章创建/修改日期。
    comments: true #为true则打开评论，false则关闭评论。
    categories: General #文章所属分类。这里分类设定为“[分类1,分类2]”。
    ---
    
    **示例**
    这是一个非常简短的内容的例子

然后重启容器。

