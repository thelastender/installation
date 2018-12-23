# Vim指南

>这篇文章是给那些对Vim没有了解，或者仅仅会基本使用Vim的人阅读的。

## 安装
### Ubuntu/Debian

```
sudo apt-get install vim-nox
```

### CentOS

```
sudo yum install vim
```

### Mac

本身自带了Vim，如果你想使用macvim，请使用下面命令。
```
brew cask install macvim
```

## 入门
基本命令的学习推荐使用vimtutor。

>一个好消息是Mac下会默认安装vimtutor，还是中文版的，所以大家直接在命令行下输入vimtutor就可以开始30分钟的学习了。

现在所有的编辑器基本都有Vim插件，例如PyCharm和GoLand都是IdeaVim，VSCode是vim。
学习Vim的最好方式就是使用，强制性让自己写所有文档和代码都是用Vim或者安装Vim插件是最好的办法。

下面列出了一些学习Vim的方式，大家感兴趣的自取。

* 游戏方式
    * [Vim Adventures](https://vim-adventures.com/)
    * [Open Vim](https://www.openvim.com/)
* 文字方式
    * [Vim 中文文档计划](https://github.com/yianwillis/vimcdoc)
* 视频方式
    * [Vim Videos - Flarfnoogins](http://derekwyatt.org/vim/tutorials/)

## Quick Reference Sheet

Vim操作命令基本上看这两个就够了，你可以下载打印出来贴到桌子上。
- [Vim Cheat Sheet](https://vim.rtorr.com/lang/zh_cn/)
- [Quick Vim](https://www.cs.cornell.edu/courses/cs312/2006fa/software/quick-vim.pdf)

## 基本配置

>所有的配置我们都放在HOME目录下的.vimrc中。

这里是我列出来的一个简单的配置，基本上配置成这样子就可以方便的使用了。

```
" 高亮
syntax on
" 查找高亮
set hlsearch
" 行号
set nu

" Set utf8 as standard encoding and en_US as the standard language
set encoding=utf8

" Use Unix as the standard file type
set ffs=unix,dos,mac

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Files, backups and undo
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Turn backup off, since most stuff is in SVN, git et.c anyway...
" 关掉备份
set nobackup
set nowb
set noswapfile

" 打开上次的位置
au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif

"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" => Text, tab and indent related
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Use spaces instead of tabs
set expandtab

" Be smart when using tabs ;)
set smarttab

" 1 tab == 4 spaces
set shiftwidth=4
set tabstop=4

" Line break on 500 characters
set lbr
set tw=500

set ai "Auto indent
set si "Smart indent
set wrap "Wrap lines

" 关闭兼容模式，下面两个是安装插件必须的
set nocompatible              " be iMproved, required
filetype off                  " required
```

## 插件
有很多种Vim插件，这里我们只讲最强大最好用的Vundle。

使用下面的命令安装：

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

然后把下面的内容加入.vimrc中：

```
" 插件
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" 你所有新的插件都必须放在这里
" 插件位置

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```

然后，你所有的插件都必须放在上面 **插件位置** 的地方。 写好了之后，打开Vim，执行：

```
:PluginInstall
```

即可安装了。

### mru.vim
[mru.vim: Plugin to manage Most Recently Used (MRU) files](https://github.com/vim-scripts/mru.vim)

### NERD Tree
[nerdtree: A tree explorer plugin for vim](https://github.com/scrooloose/nerdtree)

### lightline.vim
[lightline.vim: A light and configurable statusline/tabline plugin for Vim](https://github.com/itchyny/lightline.vim)

### indentLine
[indentLine](https://github.com/Yggdroot/indentLine)

## 懒人怎么办

如果你不想自己配置.vimrc，又想快速的使用强大的Vim，那么我推荐你直接使用 [amix/vimrc: The ultimate Vim configuration: vimrc](https://github.com/amix/vimrc)，去下载使用吧，少年。