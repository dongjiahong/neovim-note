# neovim-note

## neovim 是新版vim更好用

### 安装neovim

`brew install neovim`

neovim的配置文件夹目录应该是`/Users/$NAME/.config/nvim`,其中的配置文件为`init.vim`配置信息和方式同
vim的`.vimrc`是一样的

### 安装插件管理器plug-vim

#### 指令
`curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim`
如果拒绝链接修改host
199.232.28.133 raw.githubusercontent.com

#### 用法
在`init.nvim`中添加如下代码
```
call plug#begin('~/.vim/plugged')
Plug 'neoclide/coc.nvim', {'branch': 'release'} # 这里是你需要的插件
call plug#end()
```

#### 插件指令

`:PlugInstall` 安装配置中的插件
`:PlugUpdate` 更新插件
`:PlugClean` 删除插件

### 安装使用coc插件--用来代码提示

1. 先安装nodejs `curl -sL install-node.now.sh/lts | bash`
2. 在plug-vim安装coc插件`Plug 'neoclide/coc.nvim', {'branch': 'release'}`

### coc的配置文件`/Users/$NAME/.config/nvim/coc-settings.json`

这里我们会使用golang的配置，go-vim安装后需要安装go的工具包`:GoInstallBinaries`，其中有golang的代码提示需要使用到的`gopls`，**同时记得把go的工具包路径加入PATH**，但是我们访问`golang.org/x/tools`
时，会无法访问，目前的解决办法是使用`goproxy`

```bash
export GOPROXY=https://goproxy.io
GO111MODULE=on 
```

然后我们可以使用`:CocConfig`来配置我们的golang的服务器,它会在`.config/nvim/`目录下生成`coc-setting.json`这个配置文件具体可以参考`https://github.com/neoclide/coc.nvim/wiki/Language-servers`
