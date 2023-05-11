# **vim-lua配置文件说明**

本配置文件直接采用[nvim](https://www.bilibili.com/video/BV1WY411P736/?spm_id_from=333.788)视频的配置框架，参考[youtube](https://www.youtube.com/watch?v=ctH-a-1eUME&list=PLhoH5vyxr6Qq41NFL4GvhFp-WLd5xzIzZ)上的讲解，针对性的做了个人修改，并增加了对各种包的功能性描述，以方便之后的扩展和维护。

## UI
- 目录导航
  1. 新建文件
  2. 重命名文件
  3. 移动文件
- 切换主题
- status line

## 搜索
- 文件搜索跳转
- 字符搜索跳转 & 预览
- 代码搜索跳转 & 预览
- 搜索+替换 & 预览

## 代码导航
- 多语言支持
- 代码补全+函数签名+注释文档
- 代码引用
- 代码调用链
- 代码声明+定义，c/c++头文件源文件切换
- 符号搜索，快速跳转
- 目录大纲
- 问题诊断
- 问题分析
- code action
- 路径补全

## 调试
- 直接调试
- 调试单元测试

## Git & 本地修改历史
- diff files
- project diff
- hunk preview
- file history (git + local)

## 跳转增强
- htop

## 其他
- whichkey
- 快捷键
- 剪切板历史
- 自动恢复session

## Package说明
- [wbthomason/packer.nvim](https://github.com/wbthomason/packer.nvim)：neovim包管理器，用来管理各种package
  - 常用指令
    1. `:PackerInstall` 安装插件
    2. `:PackerUpdate` 更新插件
    3. `:PackerClean` 删除任何禁用或不再托管插件
    4. `:PackerSync` 先clean在update

- [lewis6991/impatient.nvim](https://github.com/lewis6991/impatient.nvim)：提升Neovim中加载模块的速度

- [nvim-lua/popup.nvim](https://github.com/nvim-lua/popup.nvim)：vim中popup的api接口

- [nvim-lua/plenary.nvim](https://github.com/nvim-lua/plenary.nvim)：多个插件必备的lua函数库

- [rcarriga/nvim-notify](https://github.com/rcarriga/nvim-notify)：通知管理插件
  - 常用指令
    1. `:Notifications` 显示通知消息

- [kyazdani42/nvim-web-devicons](https://github.com/nvim-tree/nvim-web-devicons)：为每个图标提供相同的图标和颜色，是vim-devicons的nvim-lua版

- [nvim-telescope/telescope.nvim](https://github.com/nvim-treesitter/nvim-treesitter)
  - 搜索工具
  - 依赖
    - [nvim-lua/plenary.nvim](https://github.com/nvim-lua/plenary.nvim)（必要）
    - [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep) (for live_grep and grep_string)
      1. 递归搜索
      2. 正则表达模式
      3. 快速，用来替代grep
      4. 用sudo来安装最简单，无超户权限需要搭载rust环境，rust安装可直接使用下载init文件进行安装，需要网络
      ```shell
      cargo build --release
      cargo install --path .
      ```
    - [sharkdp/fd](https://github.com/sharkdp/fd) (finder)
      - 速度快，类似find
      - 功能丰富简单
      - 配置同rg
    - [nvim-treesitter/nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) (finder/preview)
    - [neovim LSP](https://neovim.io/doc/user/lsp.html) (picker)
    - [devicons](https://github.com/nvim-tree/nvim-web-devicons) (icons)
  - 常用指令
    |    Mappings    |    Action    |
    |----------------|--------------|
    |   \<C-n>/\<Down> |Next item|
    |   \<C-p>/\<Up>	 |Previous item|
    |        j/k	     |Next/previous (in normal mode)|
    |       H/M/L	     |Select High/Middle/Low (in normal mode)|
    |       gg/G	     |Select the first/last item (in normal mode)|
    |      \<CR>	     |Confirm selection|
    |      \<C-x>    	 |Go to file selection as a split|
    |      \<C-v>      |Go to file selection as a vsplit|
    |      \<C-t>	     |Go to a file in a new tab|
    |      \<C-u>	     |Scroll up in preview window|
    |      \<C-d>	     |Scroll down in preview window|
    |      \<C-/>	     |Show mappings for picker actions (insert mode)|
    |        ?	       |Show mappings for picker actions (normal mode)|
    |      \<C-c>	     |Close telescope|
    |      \<Esc>	     |Close telescope (in normal mode)|
    |      \<Tab>	     |Toggle selection and move to next selection|
    |      \<S-Tab>	   |Toggle selection and move to prev selection|
    |      \<C-q>	     |Send all items not filtered to quickfixlist (qflist)|
    |      \<M-q>	     |Send all selected items to qflist|
    | | |

  - 相关插件
  
    1. [telescope-live-grep-args.nvim](https://github.com/nvim-telescope/telescope-live-grep-args.nvim) 允许传递参数
    2. [telescope-fzf-native.nvim](https://github.com/nvim-telescope/telescope-fzf-native.nvim) 模糊查找
    3. [telescope-ui-select.nvim](https://github.com/nvim-telescope/telescope-ui-select.nvim) 提供选择UI，类似`vim.ui.select`
    4. [telescope-dap.nvim](https://github.com/nvim-telescope/telescope-dap.nvim) telescope版的调试器

- [nvim-treesitter/nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)
  - 代码高亮、增量选择、格式化、折叠等
  - 常用指令
    1. `:TSInstall <language_to_install>` 安装特定的语言高亮文件
    2. `:TSInstallInfo` 显示TS安装信息
    3. `:TSUpdate {language}` 更新
    4. `:h nvim-treesitter-modules` 查看TS模块
  - 相关插件
    1. [nvim-treesitter/nvim-treesitter-textobjects](https://github.com/nvim-treesitter/nvim-treesitter-textobjects) 为类、函数、参数、条件等创建 text object 
    2. [nvim-treesitter/nvim-treesitter-context](https://github.com/nvim-treesitter/nvim-treesitter-context) 在顶端显示类和函数，romgrk/nvim-treesitter-context已搜索不到，使用官方的context

- [neovim/nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)
  - 配置和管理LSP（Language Server Protocol）
  - 提供更好的代码补全、语法检查、重构等
  - 常用指令：
    1. `:LspInfo` 显示活动和配置语言服务器的状态
  - 相关插件
    - [williamboman/nvim-lsp-installer](https://github.com/williamboman/nvim-lsp-installer) nvim-lspconfig的简单使用版，可自动下载安装各种语言的LSP
      - 当前已归档，不再更新，可使用新的williamboman/mason.nvim来代替
      - 常用指令：
        1. `:LspInstall [--sync] [server]` 安装所需LSP
        2. `:LspUninstall [--sync] [server]` 卸载所需LSP
        3. `:LspUninstallAll [--no-confirm]` 卸载所有的LSP
        4. `:LspInstallLog` 在新的tab窗口中打开日志文件
        5. `:LspPrintInstalled` 打印所有安装的LSP
    - [kosayoda/nvim-lightbulb](https://github.com/kosayoda/nvim-lightbulb) 显示当前位置可存在的代码操作建议，类似VSCODE中的灯泡图标
    - [ray-x/lsp_signature.nvim](https://github.com/ray-x/lsp_signature.nvim) 显示函数名称、参数名称、参数类型等信息

- [windwp/nvim-autopairs](https://github.com/windwp/nvim-autopairs) 自动补全括号、引号等，整合到cmp和treesitter中
- [terrortylor/nvim-comment](https://github.com/terrortylor/nvim-comment) 注释和取消注释
  - 常用指令：
    1. `CommentToggle` 注释或取消注释当前行
    2. `67,69CommentToggle` 注释或取消注释一段范围
    3. `'<,'>CommentToggle` 注释/取消注释一个选择
- [Shatur/neovim-session-manager](https://github.com/Shatur/neovim-session-manager) 保存neovim会话，可快速切换

- [hrsh7th/nvim-cmp](https://github.com/hrsh7th/nvim-cmp) 自动补全
  - 相关插件
    1. [hrsh7th/cmp-buffer](https://github.com/hrsh7th/cmp-buffer) 补全缓冲区文本
    2. [hrsh7th/cmp-path](https://github.com/hrsh7th/cmp-path) 补全系统路径
    3. [hrsh7th/cmp-cmdline](https://github.com/hrsh7th/cmp-cmdline) 补全vim命令
    4. [hrsh7th/cmp-nvim-lsp](https://github.com/hrsh7th/cmp-nvim-lsp) 补全nvim内置LSP
    5. [hrsh7th/cmp-nvim-lua](https://github.com/hrsh7th/cmp-nvim-lua) 补全lua API
    6. [saadparwaiz1/cmp-luasnip](https://github.com/saadparwaiz1/cmp_luasnip) 补全luasnip（代码段）

- [ethanholz/nvim-lastplace](https://github.com/ethanholz/nvim-lastplace) 记录上一次离开当前缓冲区时光标的位置，并在重新打开缓冲区时自动将光标放置在该位置
- [https://github.com/tpope/vim-repeat](https://github.com/tpope/vim-repeat) 扩展vim的'.'命令，能够重复更多的操作
- [tpope/vim-surround](https://github.com/tpope/vim-surround) 用于在文本周围添加、修改或删除标记
- [lukas-reineke/indent-blankline.nvim](https://github.com/lukas-reineke/indent-blankline.nvim) 在缩进处插入可定制的空白线，可视化缩进结构
- [folke/which-key.nvim](https://github.com/folke/which-key.nvim) 快速查找和学习键盘快捷键
- [phaazon/hop.nvim](https://github.com/phaazon/hop.nvim) 快速跳转位置 
  - branch = 'v2', -- optional but strongly recommended

- [L3MON4D3/LuaSnip](https://github.com/L3MON4D3/LuaSnip) 帮助用户快速插入和管理代码片段
  - 相关插件
    1. [rafamadriz/friendly-snippets](https://github.com/rafamadriz/friendly-snippets) 不同编程语言的代码片段集

- [ravenxrz/DAPInstall.nvim](https://github.com/ravenxrz/DAPInstall.nvim) 安装和配置调试器适配器协议（Debug Adapter Protocol，DAP），扩展nvim-dap的功能
  - 常用指令
    1. `:DIInstall <debugger>` 安装debugger
    2. `:DIUninstall <debugger>` 卸载debugger
    3. `:DIList` 列出已安装debugger
  - 相关插件
    1. [ravenxrz/nvim-dap](https://github.com/ravenxrz/nvim-dap) 在编辑器中使用DAP
    2. [theHamsta/nvim-dap-virtual-text](https://github.com/theHamsta/nvim-dap-virtual-text) 在代码右侧显示变量值、函数返回值等虚拟文本
    3. [rcarriga/nvim-dap-ui](https://github.com/rcarriga/nvim-dap-ui) 提供调试的UI交互
    4. [jbyuki/one-small-step-for-vimkind](https://github.com/jbyuki/one-small-step-for-vimkind) 在Neovim中调试lua代码
    5. [sakhnik/nvim-gdb](https://github.com/sakhnik/nvim-gdb) gdb for nvim，快捷键见相关网页

- [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim) git的lua实现，包括添加、删除、修改等
  - 相关插件
    1. [sindrets/diffview.nvim](https://github.com/sindrets/diffview.nvim) 比较两个版本差异

- 一些主题
  - [catppuccin/nvim](https://github.com/catppuccin/nvim)
  - [projekt0n/github-nvim-theme](https://github.com/projekt0n/github-nvim-theme) 可更新至最新版

- [nvim-tree/nvim-tree.lua](https://github.com/nvim-tree/nvim-tree.lua) Lua写的文件资源管理器插件
- [akinsho/bufferline.nvim](https://github.com/akinsho/bufferline.nvim) 在编辑器顶部提供一个缓冲行，可更新至最新版
- [nvim-lualine/lualine.nvim](https://github.com/nvim-lualine/lualine.nvim) Neovim状态栏
- [goolord/alpha-nvim](https://github.com/goolord/alpha-nvim) 自定义Neovim启动界面
- [kevinhwang91/nvim-bqf](https://github.com/kevinhwang91/nvim-bqf) better quick fix
- [RRethy/vim-illuminate](https://github.com/RRethy/vim-illuminate) 自动突出光标下的单词
- [folke/todo-comments.nvim](https://github.com/folke/todo-comments.nvim) 高亮和查找todo注释，包括TODO、HACK、PERF、NOTE、FIX、WARNING等
- [simrat39/symbols-outline](https://github.com/simrat39/symbols-outline.nvim) 符号树视图
- [aserow/tmux.nvim](https://github.com/aserowy/tmux.nvim) 在Neovim内部管理和操作tmux
- [ravenxrz/neovim-cmake](https://github.com/ravenxrz/neovim-cmake) 集成CMake
- [skanehira/preview-markdown.vim](https://github.com/skanehira/preview-markdown.vim) 在vim中预览markdown，作者不再更新
  - `:PreviewMarkdown [left|top|right|bottom|tab]`
- [voldikss/vim-translator](https://github.com/voldikss/vim-translator) vim的翻译插件
- [MTDL9/vim-log-highlighting](https://github.com/MTDL9/vim-log-highlighting) 日志高亮
- [Pocco81/HighStr.nvim](https://github.com/Pocco81/high-str.nvim) 高亮虚拟选择块
- [ravenxrz/vim-local-history](https://github.com/ravenxrz/vim-local-history) 维护文件的本地历史记录
- [vim-test/vim-test](https://github.com/vim-test/vim-test) vim测试模块
- [rcarriga/vim-ultest](https://github.com/rcarriga/vim-ultest) ultimate testing，作者已不再更新，新的repo见[Neotest](https://github.com/nvim-neotest/neotest)
- [michaelb/sniprun](https://github.com/michaelb/sniprun) 代码运行插件
- [Pocco81/auto-save.nvim](https://github.com/Pocco81/auto-save.nvim) 自动存储文件
- [djoshea/vim-autoread](https://github.com/djoshea/vim-autoread) 自动重新加载文件


## Neovim内安装

- LspInstall: ccls、pylsp、cmake、sumneko_lua
- TSInstall cpp cuda cmake make


## Q & A

- Killing git due to timeout
  - plugins.lua文件中packer.init部分添加clone时间
  ```
  git = {
    clone_timeout=3600,
  },
  ```
- Caused by: failed to fetch `https://github.com/rust-lang/crates.io-index` <CR> Caused by: failed to authenticate when downloading repository: git@github.com:rust-lang/crates.io-index
  1. 把专用密钥添加到ssh-agent的高速缓存
  2. 可手动删除密钥~/.ssh/id_xxx.pub
  ```
  eval `ssh-agent -s`
  ssh-add
  ```

