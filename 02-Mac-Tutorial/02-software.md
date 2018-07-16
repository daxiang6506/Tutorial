# Software
* [ShadowsocksX-NG](https://github.com/shadowsocks/ShadowsocksX-NG/releases/)
  > [monocloud](https://monocloud.com.au)
* [Homebrew](https://brew.sh/)
  >brew install
  >>macvim --env-std --override-system-vim  
  >>zsh zsh-completions  
  >>>* shell替换为zsh  
  >>>`chsh -s /bin/zsh`
  >>>* 安装omyzsh  
  >>>`http://ohmyz.sh/`  
  >>>* 配置zsh
  >>>```
  >>>source $HOME/.comm_profile  
  >>>ZSH_THEME="gentoo"  
  >>> alias zshconfig="vi ~/.zshrc"  
  >>> plugins=(git autojump vi-mode sublime mvn gradle colored-man colorize github jira vagrant virtualenv pip python brew osx zsh-syntax-highlighting)
  >>> alias zshconfig="vim ~/.zshrc"
  >>> alias ohmyzsh="vim ~/.oh-my-zsh"
  >>> alias cls='clear'
  >>> alias ll='ls -l'
  >>> alias la='ls -a'
  >>> alias vi='vim'
  >>> alias javac="javac -J-Dfile.encoding=utf8"
  >>> alias grep="grep --color=auto"
  >>> alias -s html=subl   # 在命令行直接输入后缀为 html 的文件名，会在 TextMate 中打开
  >>> alias -s rb=subl     # 在命令行直接输入 ruby 文件，会在 TextMate 中打开
  >>> alias -s py=subl     # 在命令行直接输入 python 文件，会用 vim 中打开，以下类似
  >>> alias -s js=subl
  >>> alias -s c=subl
  >>> alias -s java=subl
  >>> alias -s txt=subl
  >>> alias -s gz='tar -xzvf'
  >>> alias -s tgz='tar -xzvf'
  >>> alias -s zip='unzip'
  >>> alias -s bz2='tar -xjvf'
  >>> #添加zsh-completions配置:
  >>> fpath=(/usr/local/share/zsh-completions $fpath)
  >>> #You may also need to force rebuild `zcompdump`:
  >>> #rm -f ~/.zcompdump; compinit
  >>>[[ -s $(brew --prefix)/etc/profile.d/autojump.sh ]] && . $(brew --prefix)/etc/profile.d/autojump.sh
  >>> ```
  >>>* [zsh使用](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/vi-mode)  
  >>****
  >>sshfs  
  >>imagemagick  
  >>graphicsmagick  
  >>[autojump](https://www.jianshu.com/p/51e71087f732) 
  >>> `jo xxx` `j xxx` `d`  
  
* [Cask](http://caskroom.github.io/)
  >brew cask install
  >>alfred  
  >>cheatsheet  
  >>iterm2  
  >>>[github](https://github.com/mbadolato/iTerm2-Color-Schemes)  
  >>>  
  >>keka  
  >>visual-studio-code  
  >>google-chrome  
  >>pycharm  
  >>goland  
  >>intellij-idea
  >>microsoft-office
  >>osxfuse
  >>sequel-pro