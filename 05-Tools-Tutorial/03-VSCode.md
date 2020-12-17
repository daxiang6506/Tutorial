# VSCODE

## reource

* [vscode下载](https://code.visualstudio.com/Download)
* [vscode使用github](https://code.visualstudio.com/docs/editor/github)

## 快捷键

  ```bash
  * For Mac
  Ctrl + -          back一个浏览位置
  Ctrl + Shift + -  forward一个浏览位置
  F12               跳转到定义
  Ctrl + Tab        切换选项卡
  Cmd  + p          找文件
  Opt  + o          切换.cpp/.h
  Cmd  + Shift + o  显示大纲

  * For Linux
  Ctrl + Alt + -    back一个浏览位置
  Ctrl + Shift + -  forward一个浏览位置
  F12               跳转到定义
  Ctrl + Tab        切换选项卡
  Ctrl + p          找文件
  Alt  + o          切换.cpp/.h
  Ctrl + Shift + o  显示大纲

  ```

* Type Shift+Enter in the search box to insert a newline, and the search box will grow to show your full multiline query. You can also copy and paste a multiline selection from the editor into the search box.

* [VS Code C++开发常用文件过滤设置](https://blog.csdn.net/caoshiying/article/details/78165066)
* [vs Code打开新的文件会覆盖窗口中的,怎么改](https://segmentfault.com/q/1010000006131199?_ea=1023522)

## 插件

* [在vs code中使用ftp-sync插件实现客户端与服务器端代码的同步](https://blog.csdn.net/dotuian/article/details/51119650)
  > 不同的目录需要打开不同的窗口，重新初始化，否则会找到当前workspace的配置文件  
  > 操作步骤应该是在ABOX上拉代码，然后在本机上同步ABOX上的代码(保证代码权限正确，从本机上传到ABOX文件权限会有问题)
  > (删除`\\.git`，将git配置传到本机，保证本机可以push代码)
  > ，在本机上修改代码，然后选择将`当前文件同步`到ABOX上，这样可以保证各方面的同步
  
```bash
{
    "remotePath": "/home/roaddb/others/xuc/code_loc_dev_pmba/core/algorithm_vehicle_localization",
    "host": "10.69.140.235",
    "username": "roaddb",
    "password": "Test1234",
    "port": 22,
    "secure": false,
    "protocol": "sftp",
    "uploadOnSave": false,
    "passive": false,
    "debug": false,
    "privateKeyPath": null,
    "passphrase": null,
    "agent": null,
    "allow": [],
    "ignore": [
        "build",
        "dist",
        "\\.vscode",
        "\\.git",
        "\\.DS_Store"
    ],
    "generatedFiles": {
        "extensionsToInclude": [
            ""
        ],
        "path": ""
    }
}
```

* 常用

```bash
git history
git lens
vim
cmake tools
c/c++
C++ Intellisense
```

* [VS Code代码高亮颜色设置](https://blog.csdn.net/xuejinglingai/article/details/84937933)

 ```bash
 {
     "vim.useSystemClipboard": true,
     "window.zoomLevel": 1,
     "workbench.colorCustomizations": {
         "editor.selectionHighlightBackground": "#ff0000"
     }
 }
 ```

* vim 放大/缩小字体
  >ctrl+=/-

* [vim](https://blog.csdn.net/kealennieh/article/details/83592751)
  >vim和系统采用的不是相同的剪切板，所以不能直接利用ctrl+c和ctrl+v。需要进一步进行设置
  >`vim.useSystemClipboard": true`

* [How can you export VS Code extension list](https://stackoverflow.com/questions/35773299/how-can-you-export-vs-code-extension-list)