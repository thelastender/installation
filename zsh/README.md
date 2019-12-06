# Zsh

## 安装

macOS默认的shell就是zsh，如果你的不是，可以通过`chsh -s /bin/zsh`来设置成zsh。

## 插件

我安装了`oh-my-zsh`来作为主要的配置。

> https://ohmyz.sh/

通过下面的命令安装

```shell
$ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

`oh-my-zsh`会在HOME目录下创建`.zshrc`文件，这里有我的zshrc文件的示例，大家可以参考。

`oh-my-zsh`的theme我选用了bira。自己安装了`autojump`和`zsh-autosuggestions`这两个插件。

### [autojump](https://github.com/wting/autojump)安装配置

```shell
$ brew install autojump
```

把下面的内容添加到`.zshrc`末尾

```zsh
# autojump configuration
[ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
autoload -U compinit && compinit
```

然后把autojump添加到`.zshrc`的plugins里面

```shell
plugins=(git autojump)
```

### [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)安装配置

```shell
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

把zsh-autosuggestions加入到`.zshrc`的plugins里面

```shell
plugins=(git autojump zsh-autosuggestions)
```



