# Tmux Config
- [Tmux Config](#tmux-config)
    - [Tmux安装](#tmux%E5%AE%89%E8%A3%85)
    - [Tmux配置](#tmux%E9%85%8D%E7%BD%AE)

先上配置好的效果图:    
![tmux1](../img/tmux1.gif)    
![tmux2](../img/tmux2.gif)    
![tmux3](../img/tmux3.gif)    

### Tmux安装
```shell
brew install tmux
```

### Tmux配置    
安装`.tmux`配置文件，官方github地址: https://github.com/gpakosz/.tmux#installation    

- **`.tmux`安装要求**:    
  - tmux **`>= 2.1`** 
  - outside of tmux, `$TERM` must be set to `xterm-256color`    

- **`.tmux`安装** 
  按照下面命令安装: (安装之前首先备份一下 `~/.tmux.conf` 文件)    
  ```shell
  cd
  git clone https://github.com/gpakosz/.tmux.git
  ln -s -f .tmux/.tmux.conf
  cp .tmux/.tmux.conf.local .
  ```
- 然后**配置`~/.tmux.conf.local`文件**，将下列代码取消屏蔽，并将原始的屏蔽：    
  ```
  tmux_conf_theme_left_separator_main=''
  tmux_conf_theme_left_separator_sub=''
  tmux_conf_theme_right_separator_main=''
  tmux_conf_theme_right_separator_sub=''
  ```
  可以修改右侧状态栏来显示天气预报:    
  ```
  tmux_conf_theme_status_right='#{prefix}#{pairing}#{synchronized} #(curl wttr.in?format=3) , %R , %d %b | #{username}#{root} | #{hostname} '
  ```
  效果如下:    
  ![tmux4](../img/tmux5.png)    

  **更详细配置介绍[请看](tmux/tmux_conf.md)**    
  
- 官方推荐安装[`Source Code Pro`](tmux/source-code-pro-2.030R-ro-1.050R-it.zip)字体，官方[GitHub地址](https://github.com/adobe-fonts/source-code-pro/releases)或者[Powerline](https://github.com/powerline/fonts)中提供的`Source Code Pro`字体，解压后文件夹`source-code-pro/TTF/`下直接安装即可。但是安装了`Source Code Pro`字体后[安装colorls](#安装colorls)显示会有问题，所以为了兼容性**推荐 `powerline nerd-font`字体**。具体可以查看 [Nerd Font README](https://github.com/ryanoasis/nerd-fonts/blob/master/readme.md) 来获得更多安装详细介绍。    
    *Note for `iTerm2` users - Please enable the **Nerd Font** at `iTerm2 > Preferences > Profiles > Text > Non-ASCII font > mononoki Nerd Font`.*    
    ![iTerm2](../img/iTerm2.png)    
  
  
- 安装[Powerline symbols](https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf).

- 使`~/.tmux.conf.local`配置文件生效:    
  ```shell
  tmux # 启动tmux

  #然后`Ctrl+b`再按`:`进入`tmux`命令行模式
  source ~/.tmux.conf
  ```