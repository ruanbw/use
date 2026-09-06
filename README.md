
## use

### VsCode

#### 扩展

- [nginx-conf](https://marketplace.visualstudio.com/items?itemName=ahmadalli.vscode-nginx-conf) Nginx 配置高亮
- [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) Vue高亮、格式化、代码提示
- [Vue VSCode Snippets](https://marketplace.visualstudio.com/items?itemName=sdras.vue-vscode-snippets) Vue 代码片段
- [Nuxtr](https://marketplace.visualstudio.com/items?itemName=nuxtr.nuxtr-vscode) Nuxt 项目管理
- [Vitest Explorer](https://marketplace.visualstudio.com/items?itemName=vitest.explorer) Vitest 测试面板
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.liveserver) 本地静态服务器
- [Vitesse Theme](https://marketplace.visualstudio.com/items?itemName=antfu.theme-vitesse) VsCode主题
- [Catppuccin Perfect Icons](https://marketplace.visualstudio.com/items?itemName=thang-nm.catppuccin-perfect-icons) VsCode 图标 Catppuccin

[settings.json 设置](./vscode/settings.json)

### 软件

- [Clash Verge](https://www.clashverge.dev/) 科学上网
- [Docker Desktop](https://www.docker.com/products/docker-desktop) Docker 可视化
- [VsCode](https://code.visualstudio.com/) VsCode 编辑器
- [Sublime Text](https://www.sublimetext.com/) 轻量编辑器
- [IDEA](https://www.jetbrains.com/idea/) IDEA 编辑器
- [Xcode](https://developer.apple.com/xcode/) iOS/macOS 开发
- [Navicat](https://www.navicat.com/en/) Navicat 数据库
- [SourceTree](https://www.sourcetreeapp.com/) Git 可视化
- [SwitchHosts](https://github.com/oldj/SwitchHosts) hosts 管理
- [Git](https://git-scm.com/) 版本控制
- [brew](https://brew.sh/) Mac 包管理器
- [fnm](https://github.com/Schniz/fnm) Node 版本管理
- [Snipaste](https://snipaste.com/) 截图
- [Yazi](https://yazi-rs.github.io/) Yazi 终端文件浏览
- [ghostty](https://ghostty.org/) ghostty 终端
- [cleanupbuddy](https://cleanupbuddy.app/) Mac键盘清理锁定
- [IINA](https://iina.io/) 视频播放器
- [Macs Fan Control](https://github.com/crystalidea/macs-fan-control) Mac风扇控制
- [Mos](https://github.com/caldis/mos) Mac第三方鼠标平滑移动
- [Pearcleaner](https://github.com/alienator88/Pearcleaner) Mac软件清理
- [Rectangleapp](https://rectangleapp.com/) Mac分屏
- [Swish](https://highlyopinionated.co/swish/) Mac软件窗口控制

### CLI 工具

- [starship](https://starship.rs/) 终端提示符
- [atuin](https://atuin.sh/) shell 历史搜索、同步
- [gh](https://cli.github.com/) GitHub CLI
- [fd](https://github.com/sharkdp/fd) 文件查找
- [ripgrep](https://github.com/BurntSushi/ripgrep) 内容搜索
- [fzf](https://github.com/junegunn/fzf) 模糊搜索
- [zoxide](https://github.com/ajeetdsouza/zoxide) 目录跳转
- [jq](https://jqlang.github.io/jq/) JSON 处理
- [neovim](https://neovim.io/) 编辑器
- [bun](https://bun.sh/) JS 运行时、包管理
- [uv](https://docs.astral.sh/uv/) Python 包管理
- [ffmpeg](https://ffmpeg.org/) 音视频处理

### .zshrc

```sh
# maven
export MAVEN_HOME="$HOME/env/apache-maven-3.9.9"
export PATH=$MAVEN_HOME/bin:$PATH

# fnm node版本管理 $ fnm env --use-on-cd >> ~/.zshrc
export FNM_NODE_DIST_MIRROR="https://nodejs.org/dist"
export FNM_COREPACK_ENABLED="false"
export FNM_ARCH="x64"
export FNM_DIR="$HOME/.local/share/fnm"
export FNM_RESOLVE_ENGINES="false"
export FNM_LOGLEVEL="info"
export FNM_VERSION_FILE_STRATEGY="local"
eval "$(fnm env --use-on-cd)"
autoload -U add-zsh-hook
_fnm_autoload_hook () {
    if [[ -f .node-version || -f .nvmrc ]]; then
    fnm use --silent-if-unchanged
fi

}

add-zsh-hook chpwd _fnm_autoload_hook \
    && _fnm_autoload_hook

rehash

. "$HOME/.atuin/bin/env"

eval "$(atuin init zsh)"

# starship 终端状态
eval "$(starship init zsh)"

# 自动补全
source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# proxy
export NODE_USE_ENV_PROXY=1
export HTTP_PROXY=http://127.0.0.1:7890
export HTTPS_PROXY=http://127.0.0.1:7890
export NO_PROXY=127.0.0.1,localhost

# oh-my-pi (omp)
export PATH="$HOME/.bun/bin:$PATH"
```
