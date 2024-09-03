
## use

### VsCode

#### 扩展

- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) `.env`文件高亮、提示、格式化
- [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) Vue高亮、格式化、代码提示
- [UnoCss](https://marketplace.visualstudio.com/items?itemName=antfu.unocss) UnoCSS高亮、格式化
- [Vitesse Theme](https://marketplace.visualstudio.com/items?itemName=antfu.theme-vitesse) VsCode主题
- [TailwindCSS](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) TailwindCSS高亮、提示
- [Iconify IntelliSense](https://marketplace.visualstudio.com/items?itemName=antfu.iconify) Iconify 图标
- [i18n Ally](https://marketplace.visualstudio.com/items?itemName=Lokalise.i18n-ally) i18n 翻译、国际化
- [Goto definition alias](https://marketplace.visualstudio.com/items?itemName=antfu.goto-alias) 跳转到定义
- [Catppuccin Perfect Icons](https://marketplace.visualstudio.com/items?itemName=thang-nm.catppuccin-perfect-icons) VsCode 图标 Catppuccin

[settings.json 设置](./vscode/settings.json)

### 软件

- [Docker Desktop](https://www.docker.com/products/docker-desktop) Docker 可视化
- [VsCode](https://code.visualstudio.com/) VsCode 编辑器
- [IDEA](https://www.jetbrains.com/idea/) IDEA 编辑器
- [Navicat](https://www.navicat.com/en/) Navicat 数据库
- [SourceTree](https://www.sourcetreeapp.com/) Git 可视化
- [Termius](https://www.termius.com/) Termius 终端
- [Arc](https://arc.net/) Arc 浏览器
- [Clashx Pro](https://en.clashx.org/) 科学上网
- [Git](https://git-scm.com/) 版本控制
- [Warp](https://www.warp.dev/) AI 终端
- [brew](https://brew.sh/) Mac 包管理器
- [nvm](https://github.com/nvm-sh/nvm) Node 版本管理
- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh) 命令行工具
- [Applite](https://aerolite.dev/applite) brew 可视化
- [Snipaste](https://snipaste.com/) 截图

### .zshrc

```sh
# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# git clone https://github.com/denysdovhan/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
# ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
ZSH_THEME="spaceship"

# git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
# git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
# git clone https://github.com/agkozak/zsh-z $ZSH_CUSTOM/plugins/zsh-z
plugins=(
  git
  nvm
  zsh-autosuggestions
  zsh-syntax-highlighting
  zsh-z
)

# 插件nvm的配置,自动切换node版本
zstyle ':omz:plugins:nvm' lazy yes
zstyle ':omz:plugins:nvm' autoload yes
zstyle ':omz:plugins:nvm' silent-autoload yes

# https://ohmyz.sh/
source $ZSH/oh-my-zsh.sh

# maven
export MAVEN_HOME="$HOME/env/apache-maven-3.9.9"
export PATH=$PATH:$MAVEN_HOME/bin

# node版本管理
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

# jdk版本管理
export PATH="$HOME/.jenv/bin:$PATH" >> ~/.bash_profile
eval "$(jenv init -)" >> ~/.bash_profile

# 代理
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890

```
