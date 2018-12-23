# tmux说明

## 介绍

[http://louiszhai.github.io/2017/09/30/tmux/](http://louiszhai.github.io/2017/09/30/tmux/)

>基本上看上面这篇介绍文章就很清楚tmux是什么了。

## 安装

### Debian

```
sudo apt-get -t jessie-backports install tmux
```
### Mac

```
brew install tmux
```

## 配置

这里我贴上了自己的配置，大家可以直接拿去用。

如果采用ssh到开发机上，然后执行tmux使用的，虽然这样就可以保证你合上笔记本，你在开发机上的服务也在跑着，但是这样并不支持开发机到Mac的复制功能

我还做了个复制直接传递到mac上的功能，使用的是ssh反向隧道，ssh连接上开发机需要使用-R参数：

```
ssh -R 6666:localhost:22 你的开发机ip
```

大家一定要在Mac的 设置→共享 中打开远程登陆哦。

可以考虑把上面的ssh搞成alias：

```
alias ssh="ssh -R 6666:localhost:22"
```

而tmux的关于copy的配置要改成：

```
"tmux save-buffer - | ssh ender@10.1.60.138 pbcopy"
```

>如果你使用VPN的话，跨机器的copy和paste就暂时不会生效哦。

Mac本地的复制需要安装[reattach-to-user-namespace](https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard) 才会生效，大家使用`brew install reattach-to-user-namespace`即可。