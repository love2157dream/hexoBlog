---
title: SublimeText3配置NodeJs环境
date: 2017-12-22 11:02:14
tags: SublimeText3
categories: SublimeText3
---

 
# 手动安装

通过地址[SublimeText-Nodejs](https://github.com/tanepiper/SublimeText-Nodejs)去github上下载该包，解压放到Sublime Text3/Packages目录下

## 修改配置文件

 > 在 `Sublie Text 3 Packages` 文件目录下， 找到 `Nodejs.sublime-settings` 文件，更改内容如下：

```json
{
  // save before running commands
  "save_first": true,
  // if present, use this command instead of plain "node"
  // e.g. "/usr/bin/node" or "C:\bin\node.exe"
  "node_command": "M:\\nodejs\\node.exe",
  // Same for NPM command
  "npm_command": "M:\\nodejs\\npm.cmd",
  // as 'NODE_PATH' environment variable for node runtime
  "node_path": false,
  "expert_mode": false,
  "output_to_new_tab": false
}
```

**注: 修改了两个地方，分别是 `node_command` 和 `npm_command`**

 > 在 `Sublie Text 3 Packages` 文件目录下， 找到 `Nodejs.sublime-build` 文件，更改内容如下：

```json
    "cmd": ["node", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.js",
    "shell":true,
    "encoding": "utf8",
    "windows": {
        "cmd": ["taskkill","/F", "/IM", "node.exe","&","node", "$file"]
    },
    "linux": {
        "cmd": ["killall node; node", "$file"]
    },
    "osx": {
        "cmd": ["killall node; node $file"]
    }
}
```
**注: 修改了两个地方，分别是 `encoding` 和 windows 下的`cmd` ,windows 下的cmd命令是每次执行的时候都会kill 掉以前启动的nodejs 进程，这个命令有些错误，我们修改它，到达我们想要的效果**

## 测试

新建一个 test.js 文件 输入以前内容

```javascript
var http = require('http');
var os = require('os');
 
http.createServer(function (request, response) {
  response.writeHead(200, {'Content-Type': 'text/plain'});
  response.end('Hello World\n');
 
}).listen(3000);
 
console.log('Server running at http://127.0.0.1:3000/');  
```

`Ctrl +B` 编译一下，会在Sublime Text 控制台 看到 `Server running at http://127.0.0.1:3000/` ，接下来我们从浏览器打开 访问 `http://127.0.0.1:3000/` .