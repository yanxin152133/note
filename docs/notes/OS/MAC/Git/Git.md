# 1. Mac终端设置Git命令补全
## 1.1. .zshrc
编辑`.zshrc`文件。

```bash
sudo vi ~/.zshrc
```

添加以下内容：

```html
autoload -Uz compinit && compinit
```

使之生效。

```bash
source ~/.zsrc
```

### 1.1.1. zsh compinit: insecure directories and files, run compaudit for list.
#### 1.1.1.1. 参考
[zsh compinit: insecure directories and files, run compaudit for list.](https://github.com/zsh-users/zsh-completions/issues/433)

## 1.2. on my zsh (可选)
### 1.2.1. 安装Homebrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 1.2.2. 升级zsh、zsh-completions
```bash
brew install zsh zsh-completions
```

### 1.2.3. 安装on my zsh
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
or
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

### 1.2.4. 配置on my zsh
#### 1.2.4.1. Theme
[Themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)

#### 1.2.4.2. 插件
[插件](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)


