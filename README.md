# vimrc
vim's personal setting

## 1. 源码安装编辑器vim

```
git clone git@github.com:vim/vim.git
cd vim/
./configure --with-features=huge --enable-pythoninterp --enable-rubyinterp --enable-luainterp --enable-perlinterp --with-python-config-dir=/usr/lib/python2.7/config/ --enable-cscope --prefix=/usr
make
make install
```
其中，--enable-pythoninterp、--enable-rubyinterp、--enable-perlinterp、--enable-luainterp 等分别表示支持 ruby、python、perl、lua 编写的插件，--enable-cscope 支持 cscope，--with-python-config-dir=/usr/lib/python2.7/config/ 指定 python 路径，这几个特性非常重要，影响后面各类插件的使用。其中要事先安装的相关依赖库有libx11-dev，ruby-dev，libncurses5-dev，lua5.1-policy-dev，python-dev，libperl-dev。

## 2. 插件管理工具vundle
`git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim`

.vimrc添加相关配置信息
```
" vundle 环境设置
filetype off
set rtp+=~/.vim/bundle/Vundle.vim
" vundle 管理的插件列表必须位于 vundle#begin() 和 vundle#end() 之间
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'
Plugin 'Valloric/YouCompleteMe'
Plugin 'altercation/vim-colors-solarized'
Plugin 'octol/vim-cpp-enhanced-highlight'
Plugin 'vim-airline/vim-airline'
Plugin 'derekwyatt/vim-fswitch'
Plugin 'vim-airline/vim-airline-themes'
Plugin 'nathanaelkane/vim-indent-guides'
Plugin 'kshenoy/vim-signature'
Plugin 'majutsushi/tagbar'
Plugin 'scrooloose/nerdtree'
Plugin 'scrooloose/nerdcommenter'
Plugin 'SirVer/ultisnips'
Plugin 'honza/vim-snippets'
Plugin 'tpope/vim-surround'
Plugin 'jiangmiao/auto-pairs'
Plugin 'vim-scripts/indexer.tar.gz' 
Plugin 'vim-scripts/DfrankUtil'
Plugin 'vim-scripts/vimprj'
Plugin 'ctrlpvim/ctrlp.vim'
"Python
Plugin 'scrooloose/syntastic'
Plugin 'nvie/vim-flake8'
Plugin 'vim-scripts/indentpython.vim'
" 插件列表结束
call vundle#end()
filetype plugin indent on
```
其中`Plugin 'Valloric/YouCompleteMe'`对应一个插件
`:PluginInstall``:PluginUpdate``:PluginClean`分别是安装，更新，删除相关插件

## 3. YCM补全插件配置
[来源](https://github.com/Valloric/YouCompleteMe)
>### Ubuntu Linux x64

>These instructions (using install.py) are the quickest way to install YouCompleteMe, however they may not work for everyone. >If the following instructions don't work for you, check out the full installation guide.
>
>Make sure you have Vim 7.4.1578 with Python 2 or Python 3 support. Ubuntu 16.04 and later have a Vim that's recent enough. >You can see the version of Vim installed by running vim --version. If the version is too old, you may need to compile Vim >from source (don't worry, it's easy).
>
>Install YouCompleteMe with Vundle.
>
>Remember: YCM is a plugin with a compiled component. If you update YCM using Vundle and the ycm_core library APIs have >changed (happens rarely), YCM will notify you to recompile it. You should then rerun the install process.
>
>Install development tools and CMake:
>
>sudo apt-get install build-essential cmake
>Make sure you have Python headers installed:
>
>sudo apt-get install python-dev python3-dev
>Compiling YCM with semantic support for C-family languages:
>
>cd ~/.vim/bundle/YouCompleteMe
>./install.py --clang-completer
>Compiling YCM without semantic support for C-family languages:
>
>cd ~/.vim/bundle/YouCompleteMe
>./install.py
>The following additional language support options are available:
>
>C# support: install Mono and add --omnisharp-completer when calling ./install.py.
>Go support: install Go and add --gocode-completer when calling ./install.py.
>TypeScript support: install Node.js and npm then install the TypeScript SDK with npm install -g typescript.
>JavaScript support: install Node.js and npm and add --tern-completer when calling ./install.py.
>Rust support: install Rust and add --racer-completer when calling ./install.py.
>To simply compile with everything enabled, there's a --all flag. So, to install with all language features, ensure xbuild, >go, tsserver, node, npm, rustc, and cargo tools are installed and in your PATH, then simply run:
>
>cd ~/.vim/bundle/YouCompleteMe
>./install.py --all
>That's it. You're done. Refer to the User Guide section on how to use YCM. Don't forget that if you want the C-family >semantic completion engine to work, you will need to provide the compilation flags for your project to YCM. It's all in the >User Guide.
>
>YCM comes with sane defaults for its options, but you still may want to take a look at what's available for configuration. >There are a few interesting options that are conservatively turned off by default that you may want to turn on.

