# vim
vim前端、后端插件.

```javascript
1、将下面的配置文件拷入~/.vimrc
2、安装https://github.com/junegunn/vim-plug
  curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
3、进入vim
  shift+:输入PlugInstall回车, 会自动导入~/.vimrc中设置的插件
```

```javascript
"设置环境变量(所有插件都可以这样引用).
set runtimepath^=~/.vim/bundle/ag "引入ag
set runtimepath^=~/.vim/bundle/vim-airline-themes "引入ariline-themes

"设置缩进.
set tabstop=4
set softtabstop=4
set shiftwidth=4
set autoindent
set cindent
set expandtab

"nerdtree.
map <F3> :NERDTreeMirror<CR>
map <F3> :NERDTreeToggle<CR>
let g:NERDTreeDirArrowExpandable = '▸'
let g:NERDTreeDirArrowCollapsible = '▾'


"ctrlp.
set runtimepath^=~/.vim/bundle/ctrlp.vim

"ctrlp-func.
nnoremap <Leader>fu :CtrlPFunky<Cr>
"narrow the list down with a word under cursor
nnoremap <Leader>fU :execute 'CtrlPFunky ' . expand('<cword>')<Cr>
let g:ctrlp_funky_matchtype = 'path'
let g:ctrlp_funky_syntax_highlight = 1

"主题.
"colorscheme peachpuff
colorscheme desert

"语法.
syntax enable
syntax on

"vim-plug.
" Specify a directory for plugins (for Neovim: ~/.local/share/nvim/plugged)
call plug#begin('~/.vim/plugged')

" Make sure you use single quotes

" Shorthand notation; fetches https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

" Any valid git URL is allowed
Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" Multiple Plug commands can be written in a single line using | separators
Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-master branch
Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
Plug 'fatih/vim-go', { 'tag': '*' }

" Plugin options
Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
Plug '~/my-prototype-plugin'

" Initialize plugin system
call plug#end()

"ctrlsf.
let g:ctrlsf_ackprg = 'ag'
let g:ctrlsf_auto_close = 0
let g:ctrlsf_case_sensitive = 'no'
let g:ctrlsf_context = '-B 5 -A 3'
let g:ctrlsf_default_root = 'project'
let g:ctrlsf_extra_backend_args = {
    \ 'pt': '--home-ptignore'
    \ }
let g:ctrlsf_mapping = {
    \ "next": "n",
    \ "prev": "N",
    \ }
let g:ctrlsf_populate_qflist = 1
let g:ctrlsf_regex_pattern = 1
let g:ctrlsf_position = 'bottom'
let g:ctrlsf_winsize = '30%'

"ag.
let g:ag_prg="<custom-ag-path-goes-here> --vimgrep"
let g:ag_working_path_mode="r"

"the_silver_searcher.
let g:ackprg = 'ag --nogroup --nocolor --column'

"airline.
set laststatus=2
let g:airline#extensions#tabline#enabled = 1     "开启tabline
let g:airline#extensions#tabline#left_sep = ' '    "tabline中当前buffer两端的分隔字符
let g:airline#extensions#tabline#left_alt_sep = '|'    "tabline中未激活buffer两端的分隔字符
"let g:airline_powerline_fonts = 1 "使用powerline打过补丁的字体
let g:airline_powerline_fonts = 'Symbol Neu Powerline'
let g:airline#extensions#tabline#buffer_nr_show = 1    "tabline中buffer显示编号
let g:airline_section_b = '%{strftime("%c")}'
let g:airline_section_y = 'BN: %{bufnr("%")}'

"映射切换buffer的键位
nnoremap [b :bp<CR>
nnoremap ]b :bn<CR>
"映射<leader>num到num buffer
map <leader>1 :b 1<CR>
map <leader>2 :b 2<CR>
map <leader>3 :b 3<CR>
map <leader>4 :b 4<CR>
map <leader>5 :b 5<CR>
map <leader>6 :b 6<CR>
map <leader>7 :b 7<CR>
map <leader>8 :b 8<CR>
map <leader>9 :b 9<CR>


"airline-theme.
let g:airline_theme='badwolf'

"vim-multiple-cursors.
let g:multi_cursor_use_default_mapping=0
"Default mapping
let g:multi_cursor_next_key='<C-n>'
let g:multi_cursor_prev_key='<C-p>'
let g:multi_cursor_skip_key='<C-x>'
let g:multi_cursor_quit_key='<Esc>'

"let g:multi_cursor_start_key='<C-n>'
"let g:multi_cursor_start_word_key='g<C-n>'
nnoremap <silent> <M-j> :MultipleCursorsFind <C-R>/<CR>
vnoremap <silent> <M-j> :MultipleCursorsFind <C-R>/<CR>
```

```html
------------------------------------------------------------
多窗口切换快捷键：ctrl + ww
------------------------------------------------------------
◎ vsp(纵屏).
----------------
:vsp 文件名
------
例如：
------
:vsp member.php
------------------------------------------------------------
◎ new(横屏).
----------------
:new 文件名
------
例如：
------
:new member.php
------------------------------------------------------------
```
