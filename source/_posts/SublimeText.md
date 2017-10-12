---
title: SublimeText3
date: 2017-10-12 09:58:34
tags: 
    - SublimeText3
    - SublimeText3插件
    - SublimeText3快捷键
categories: SublimeText3
---
## 官网

- http://www.sublimetext.com/

## 插件

- https://packagecontrol.io

## 插件控制台安装  

### Package Control 安装  
方式一：  
    1.控制台是通过快捷键[ctrl+`]  
    2.视图 > 显示控制台菜单访问的。一旦打开，将下面的Python代码粘贴到控制台中。点击回车进行安装  
``` Python
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

方式二：  
    1.点击`Preferences>Browse Packages...`菜单   
    2.浏览了一个文件夹中，然后到`Installed Packages/`文件夹   
    3.下载包[Package Control.sublime-package](https://packagecontrol.io/Package%20Control.sublime-package)并复制到`Installed Packages/`的目录  
    4.重启Sublime Text  


## 快捷键介绍

### 选择类

     Ctrl+D 选中光标所占的文本，继续操作则会选中下一个相同的文本。  
     Alt+F3 选中文本按下快捷键，即可一次性选择全部的相同文本进行同时编辑。举个栗子：快速选中并更改所有相同的变量名、函数名等。
     Ctrl+L 选中整行，继续操作则继续选择下一行，效果和 Shift+↓ 效果一样。
     Ctrl+Shift+L 先选中多行，再按下快捷键，会在每行行尾插入光标，即可同时编辑这些行。
     Ctrl+Shift+M 选择括号内的内容（继续选择父括号）。举个栗子：快速选中删除函数中的代码，重写函数体代码或重写括号内里的内容。
     Ctrl+M 光标移动至括号内结束或开始的位置。
     Ctrl+Enter 在下一行插入新行。举个栗子：即使光标不在行尾，也能快速向下插入一行。
     Ctrl+Shift+Enter 在上一行插入新行。举个栗子：即使光标不在行首，也能快速向上插入一行。
     Ctrl+Shift+[ 选中代码，按下快捷键，折叠代码。
     Ctrl+Shift+] 选中代码，按下快捷键，展开代码。
     Ctrl+K+0 展开所有折叠代码。
     Ctrl+← 向左单位性地移动光标，快速移动光标。
     Ctrl+→ 向右单位性地移动光标，快速移动光标。
     shift+↑ 向上选中多行。
     shift+↓ 向下选中多行。
     Shift+← 向左选中文本。
     Shift+→ 向右选中文本。
     Ctrl+Shift+← 向左单位性地选中文本。
     Ctrl+Shift+→ 向右单位性地选中文本。
     Ctrl+Shift+↑ 将光标所在行和上一行代码互换（将光标所在行插入到上一行之前）。
     Ctrl+Shift+↓ 将光标所在行和下一行代码互换（将光标所在行插入到下一行之后）。
     Ctrl+Alt+↑ 向上添加多行光标，可同时编辑多行。
     Ctrl+Alt+↓ 向下添加多行光标，可同时编辑多行。


### 编辑类

    Ctrl+J 合并选中的多行代码为一行。举个栗子：将多行格式的CSS属性合并为一行。
    Ctrl+Shift+D  复制光标所在整行，插入到下一行。
    Tab 向右缩进。
    Shift+Tab 向左缩进。
    Ctrl+K+K 从光标处开始删除代码至行尾。
    Ctrl+Shift+K 删除整行。
    Ctrl+/ 注释单行。
    Ctrl+Shift+/ 注释多行。
    Ctrl+K+U 转换大写。
    Ctrl+K+L 转换小写。
    Ctrl+Z 撤销。
    Ctrl+Y 恢复撤销。
    Ctrl+U 软撤销，感觉和 Gtrl+Z 一样。
    Ctrl+F2 设置书签
    Ctrl+T 左右字母互换。
    F6 单词检测拼写 
 

### 搜索类 

    Ctrl+F 打开底部搜索框，查找关键字。
    Ctrl+shift+F 在文件夹内查找，与普通编辑器不同的地方是sublime允许添加多个文件夹进行查找，略高端，未研究。
    Ctrl+P 打开搜索框。举个栗子：1、输入当前项目中的文件名，快速搜索文件，2、输入@和关键字，查找文件中函数名，3、输入：和数字，跳转到文件中该行代码，4、输入#和关键字，查找变量名。
    Ctrl+G 打开搜索框，自动带：，输入数字跳转到该行代码。举个栗子：在页面代码比较长的文件中快速定位。
    Ctrl+R 打开搜索框，自动带@，输入关键字，查找文件中的函数名。举个栗子：在函数较多的页面快速查找某个函数。
    Ctrl+： 打开搜索框，自动带#，输入关键字，查找文件中的变量名、属性名等。
    Ctrl+Shift+P 打开命令框。场景栗子：打开命名框，输入关键字，调用sublime text或插件的功能，例如使用package安装插件。
    Esc 退出光标多行选择，退出搜索框，命令框等。
 

### 显示类 

    Ctrl+Tab 按文件浏览过的顺序，切换当前窗口的标签页。
    Ctrl+PageDown 向左切换当前窗口的标签页。
    Ctrl+PageUp 向右切换当前窗口的标签页。
    Alt+Shift+1 窗口分屏，恢复默认1屏（非小键盘的数字）
    Alt+Shift+2 左右分屏-2列
    Alt+Shift+3 左右分屏-3列
    Alt+Shift+4 左右分屏-4列
    Alt+Shift+5 等分4屏
    Alt+Shift+8 垂直分屏-2屏
    Alt+Shift+9 垂直分屏-3屏
    Ctrl+K+B 开启/关闭侧边栏。
    F11 全屏模式
    Shift+F11 免打扰模式

## 插件介绍

### [MarkDown Editing](https://github.com/SublimeText-Markdown/MarkdownEditing):支持Markdown语法高亮;支持Github Favored Markdown语法;  

### [MarkdownPreview](https://github.com/revolunet/sublimetext-markdown-preview):按CTRL + B生成网页HTML；在最前面添加[TOC]自动生成目录；  

### [Markdown Extended](https://github.com/jonschlinkert/sublime-markdown-extended) + [Extends Monokai](https://github.com/jonschlinkert/sublime-monokai-extended):不错的Markdown主题，支持对多种语言的高亮  

### [OmniMarkupPreviwer](http://theo.im/OmniMarkupPreviewer/):实时在浏览器中预，而MarkdownPreview是需要手动生成的和F5的。览如果双屏的话，应该具有不错的体验。快捷键如下：    

    Ctrl+Alt+O: Preview Markup in Browser.

    Ctrl+Alt+X: Export Markup as HTML. 

    Ctrl+Alt+C: Copy Markup as HTML.  

### [WordCount](https://github.com/titoBouzout/WordCount):可以实时显示当前文件的字数。  

### [ConvertToUTF8](https://github.com/seanliang/ConvertToUTF8):解决 Sublime Text的乱码问题  
  
### [Side​Bar​Enhancements](https://github.com/sidebarenhancements-org/sidebarenhancements):加强侧边栏    

### [BracketHighlighter](https://github.com/facelessuser/BracketHighlighter):显示我在哪个括号内  
 
### [Emmet](https://github.com/sergeche/emmet-sublime): html编码快速补全，[Emmet Doc](https://docs.emmet.io/cheat-sheet/)快捷键配置  

``` json
    {
      "keys": ["tab"], 
      "command": "expand_abbreviation_by_tab", 

      // put comma-separated syntax selectors for which 
      // you want to expandEmmet abbreviations into "operand" key 
      // instead of SCOPE_SELECTOR.
      // Examples: source.js, text.html - source
      "context": [
        {
          "operand": "SCOPE_SELECTOR", 
          "operator": "equal", 
          "match_all": true, 
          "key": "selector"
        }, 

        // run only if there's no selected text
        {
          "match_all": true, 
          "key": "selection_empty"
        },

        // don't work if there are active tabstops
        {
          "operator": "equal", 
          "operand": false, 
          "match_all": true, 
          "key": "has_next_field"
        }, 

        // don't work if completion popup is visible and you
        // want to insert completion with Tab. If you want to
        // expand Emmet with Tab even if popup is visible -- 
        // remove this section
        {
          "operand": false, 
          "operator": "equal", 
          "match_all": true, 
          "key": "auto_complete_visible"
        }, 
        {
          "match_all": true, 
          "key": "is_abbreviation"
        }
      ]
    }
```

## 自定义快捷键设置

### 删除当前行

``` json
    {
        "keys": ["ctrl+d"],
        "command":"run_macro_file",
        "args": {"file":"Packages/Default/Delete Line.sublime-macro"}
    }
```

### 复制文件路径

``` json
    { "keys": ["ctrl+shift+c"], "command": "copy_path" }
```

### 打开文件所在文件夹

``` json
    { "keys": ["ctrl+shift+t"], "command": "open_terminal" }
```

### 打开文件所在项目的根目录文件夹

``` json
    { "keys": ["ctrl+shift+alt+t"], "command": "open_terminal_project_folder" }
```

### chrome浏览器预览

``` json
    { "keys": ["f2"], "command": "side_bar_files_open_with",
        "args": {
                "paths": [],
                "application": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe",
                "extensions":".*"
        }
    }
```

### 是否自动换行

``` json
    { "keys": ["f8"], "command": "toggle_setting", "args": {"setting": "word_wrap"}}
```
