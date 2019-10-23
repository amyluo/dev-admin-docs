#Using plug.vim

##Download `plug.vim` and put it in `~/.vim/autoload`
```
$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
## Edit your `~/.vimrc` file
Added below block
```
" ==== vim-plug settings begin ====

" Refer to https://github.com/junegunn/vim-plug
" - Avoid using standard Vim directory names like 'plugin'
" ---- examples begin ----"
" Make sure you use single quotes
" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
" Plug 'junegunn/vim-easy-align'
" Any valid git URL is allowed
" Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" Multiple Plug commands can be written in a single line using | separators
" Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading
" Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
" Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-master branch
" Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
" Plug 'fatih/vim-go', { 'tag': '*' }

" Plugin options
" Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
" Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
" Plug '~/my-prototype-plugin'
" ---- examples end ----"

" Specify a directory for plugins
call plug#begin('~/.vim/plugged')

Plug 'https://github.com/itchyny/lightline.vim'
Plug 'https://github.com/tpope/vim-commentary.git'
Plug 'https://github.com/tpope/vim-surround.git'
Plug 'https://github.com/tpope/vim-eunuch.git'
Plug 'https://github.com/tpope/vim-fugitive.git'
Plug 'https://github.com/terryma/vim-multiple-cursors.git'
Plug 'https://github.com/sheerun/vim-polyglot.git'
Plug 'https://github.com/plasticboy/vim-markdown.git'
Plug 'https://github.com/ConradIrwin/vim-bracketed-paste.git'
Plug 'https://github.com/mbbill/undotree.git'
Plug 'https://github.com/airblade/vim-gitgutter.git'
Plug 'https://github.com/pangloss/vim-javascript.git'
Plug 'https://github.com/majutsushi/tagbar.git'
Plug 'https://github.com/junegunn/limelight.vim.git'
Plug 'https://github.com/scrooloose/nerdtree.git'
Plug 'https://github.com/tpope/vim-repeat.git'
Plug 'https://github.com/junegunn/vim-fnr.git'
Plug 'https://github.com/Yggdroot/indentLine.git'


" Initialize plugin system
call plug#end()

" ==== vim-plug settings end ====
```
##The reload `.vimrc` and start a `vim` window, then run `:PlugInstall` to install plugins
