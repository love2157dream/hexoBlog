---
title: 利用hexo和github搭建博客
date: 2017-10-16 10:02:56
tags: 
    - hexo
    - github
    - 博客
categories: hexo
---

# 安装

需要安装Node.js,Git,然后利用npm完成Hexo的安装

``` bash
    $ npm install -g hexo-cli
```

# 建站

安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

``` bash
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建完成后，指定文件夹的目录如下： 

``` 
.
├── .deploy       # 执行hexo deploy命令部署到GitHub上的内容目录
├── public        # 执行hexo generate命令，输出的静态网页内容目录
├── scaffolds     # layout模板文件目录，其中的md文件可以添加编辑
├── scripts       # 扩展脚本目录，这里可以自定义一些javascript脚本
├── source        # 文章源码目录，该目录下的markdown和html文件均会被hexo处理。该页面对应repo的根目录，404文件、favicon.ico文件，CNAME文件等都应该放这里，该目录下可新建页面目录。
|   ├── _drafts   # 草稿文章
|   └── _posts    # 发布文章
├── themes        # 主题文件目录
├── _config.yml   # 全局配置文件，大多数的设置都在这里
└── package.json  # 应用程序数据，指明hexo的版本等信息，类似于一般软件中的关于信息
```


# 新建文章  

执行new命令，生成指定名称的文章至hexo\source\_posts\postName.md。

``` bash
$ hexo new [layout] "postName" #新建文章
```

Hexo 有三种默认布局：post、page 和 draft，它们分别对应不同的路径，而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。

    布局  路径
    post    source/_posts
    page    source
    draft   source/_drafts

## 布局（Layout）

Hexo 有三种默认布局：post、page 和 draft，它们分别对应不同的路径，而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。
 

## 文件名称

Hexo 默认以标题做为文件名称，但您可编辑 new_post_name 参数来改变默认的文件名称，举例来说，设为 :year-:month-:day-:title.md 可让您更方便的通过日期来管理文章。

    变量  描述
    :title  标题（小写，空格将会被替换为短杠）
    :year   建立的年份，比如， 2015
    :month  建立的月份（有前导零），比如， 04
    :i_month    建立的月份（无前导零），比如， 4
    :day    建立的日期（有前导零），比如， 07
    :i_day  建立的日期（无前导零），比如， 7


## 草稿

刚刚提到了 Hexo 的一种特殊布局：draft，这种布局在建立时会被保存到 source/_drafts 文件夹，您可通过 publish 命令将草稿移动到 source/_posts 文件夹，该命令的使用方式与 new 十分类似，您也可在命令中指定 layout 来指定布局。

``` bash 
$ hexo publish [layout] <title>
```

草稿默认不会显示在页面中，您可在执行时加上 --draft 参数，或是把 render_drafts 参数设为 true 来预览草稿。

## 模版（Scaffold）
在新建文章时，Hexo 会根据 scaffolds 文件夹内相对应的文件来建立文件，例如：
``` bash 
$ hexo new photo "My Gallery"
在执行这行指令时，Hexo 会尝试在 scaffolds 文件夹中寻找 photo.md，并根据其内容建立文章，以下是您可以在模版中使用的变量：
```

    变量  描述
    layout  布局
    title   标题
    date    文件建立日期

    
# 命令

###  int 

``` bash
$ hexo init [folder]
```

新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

###  new  

``` bash
$ hexo new [layout] <title>
```

新建一篇文章。如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

###  generate 

``` bash
$ hexo generate
```

生成静态文件。

    选项  描述
    -d, --deploy    文件生成后立即部署网站
    -w, --watch 监视文件变动
    该命令可以简写为
    $ hexo g

###  publish  

``` bash
$ hexo publish [layout] <filename>
发表草稿。
```

###  server  

``` bash
$ hexo server
```

启动服务器。默认情况下，访问网址为： http://localhost:4000/。

    选项  描述
    -p, --port  重设端口
    -s, --static    只使用静态文件
    -l, --log   启动日记记录，使用覆盖记录格式

###  deploy

``` bash
$ hexo deploy
```

部署网站。

    参数  描述
    -g, --generate  部署之前预先生成静态文件
    该命令可以简写为：
    $ hexo d

###  render  

``` bash
$ hexo render <file1> [file2] ...
```

渲染文件。

    参数  描述
    -o, --output    设置输出路径

###  migrate

``` bash
$ hexo migrate <type>
```

从其他博客系统 迁移内容。

###  clean  

``` bash
$ hexo clean
```

清除缓存文件 (db.json) 和已生成的静态文件 (public)。
在某些情况（尤其是更换主题后），如果发现您对站点的更改无论如何也不生效，您可能需要运行该命令。

###  list  

``` bash
$ hexo list <type>
```

列出网站资料。

###  version

``` bash
$ hexo version
```

显示 Hexo 版本。

###  选项  

####  安全模式  

``` bash
$ hexo --safe
```

在安全模式下，不会载入插件和脚本。当您在安装新插件遭遇问题时，可以尝试以安全模式重新执行。 

####  调试模式  

``` bash
$ hexo --debug
```

在终端中显示调试信息并记录到 debug.log。当您碰到问题时，可以尝试用调试模式重新执行一次，并 提交调试信息到 GitHub。

####  简洁模式  

``` bash
$ hexo --silent
```

隐藏终端信息。

####  自定义配置文件的路径  

``` bash
$ hexo --config custom.yml
```

自定义配置文件的路径，执行后将不再使用 _config.yml。

####  显示草稿  

``` bash
$ hexo --draft
```

显示 source/_drafts 文件夹中的草稿文章。

####  自定义 CWD 

``` bash
$ hexo --cwd /path/to/cwd
```

自定义当前工作目录（Current working directory）的路径。  



