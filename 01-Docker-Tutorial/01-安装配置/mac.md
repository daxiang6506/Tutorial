## 安装
使用 Homebrew 安装`brew cask install docker`

## 配置
1. [docker for Mac的配置有bug,直接通过UI来设置会出问题](_images/mac-config-gui.png)  
2. [解决的方法是直接修改daemon.json文件里的内容,同时,"Securely store logins in macOS"去掉勾选，不然也会出问题](_images/mac-config-term.png)
3. [启动KiteMatic出错](_images/KiteMactic-error.png)  
   [修复流程](_images/Kitematic-config.png)  
   [Kitematic下载地址](https://github.com/docker/kitematic/releases)