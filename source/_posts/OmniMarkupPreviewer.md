---
title: Sublime3插件OmniMarkupPreviewer预览Markdown文件提示Error:404 Not Found
date: 2017-10-13 09:38:21
tags: 
    - SublimeText3
    - SublimeText3插件
categories: SublimeText3
---


#### 在安装完成后，直接进行预览时发现浏览器中给出如下错误信息

    **Error**: 404 Not Found
    Sorry, the requested URL 'http://127.0.0.1:51004/view/28' caused an error:

    'buffer_id(28) is not valid (closed or unsupported file format)'

    **NOTE:** If you run multiple instances of Sublime Text, you may want to adjust
    the `server_port` option in order to get this plugin work again.

#### 方案1：
在用户设置中增加以下内容Preferences > Package Settings > OmniMarkupPreviewer > Settings – User

    {
        "renderer_options-MarkdownRenderer": {
            "extensions": ["tables", "fenced_code", "codehilite"]
        }
    }
保存后重启生效。

#### 方案2：
修改mdx_strikeout.py文件内容,文件位置

    Mac: "/Users/<username>/Library/Application Support/Sublime Text 3/Packages/OmniMarkupPreviewer/OmniMarkupLib/Renderers/libs/mdx_strikeout.py"
    Windows："C:\Users\{UserName}\AppData\Roaming\Sublime Text 3\Packages\OmniMarkupPreviewer\OmniMarkupLib\Renderers\libs\mdx_strikeout.py"
将最后一个函数:

    def makeExtension(configs=None):
        return StrikeoutExtension(configs=configs)
替换为如下内容

    def makeExtension(*args, **kwargs):
        return StrikeoutExtension(*args, **kwargs)
