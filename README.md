
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

### Docker

[详情](./docker.md)

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
  zsh-autosuggestions
  zsh-syntax-highlighting
  zsh-z
)

# https://ohmyz.sh/
source $ZSH/oh-my-zsh.sh

# maven
export MAVEN_HOME="$HOME/env/apache-maven-3.9.9"
export PATH=$MAVEN_HOME/bin:$PATH

# jdk版本管理
export PATH="$HOME/.jenv/bin:$PATH" >> ~/.bash_profile
eval "$(jenv init -)" >> ~/.bash_profile

# 代理
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890

# pnpm
export PNPM_HOME="/Users/ruanbw/Library/pnpm"
case ":$PATH:" in
  *":$PNPM_HOME:"*) ;;
  *) export PATH="$PNPM_HOME:$PATH" ;;
esac
# pnpm end

# fnm node版本管理 $ fnm env --use-on-cd >> ~/.zshrc
export PATH="/Users/ruanbw/.local/state/fnm_multishells/33580_1727423774832/bin":$PATH
export FNM_NODE_DIST_MIRROR="https://nodejs.org/dist"
export FNM_COREPACK_ENABLED="false"
export FNM_ARCH="x64"
export FNM_DIR="/Users/ruanbw/.local/share/fnm"
export FNM_RESOLVE_ENGINES="false"
export FNM_MULTISHELL_PATH="/Users/ruanbw/.local/state/fnm_multishells/33580_1727423774832"
export FNM_LOGLEVEL="info"
export FNM_VERSION_FILE_STRATEGY="local"
autoload -U add-zsh-hook
_fnm_autoload_hook () {
    if [[ -f .node-version || -f .nvmrc ]]; then
    fnm use --silent-if-unchanged
fi

}

add-zsh-hook chpwd _fnm_autoload_hook \
    && _fnm_autoload_hook

rehash

# atuin shell history
# curl --proto '=https' --tlsv1.2 -LsSf https://setup.atuin.sh | sh
```
