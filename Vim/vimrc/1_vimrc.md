# 1_vimrc

## vimrc简介

```
# open cmd
$ vim --version
>>>
   system vimrc file: "$VIM\vimrc"
     user vimrc file: "$HOME\_vimrc"
 2nd user vimrc file: "$HOME\vimfiles\vimrc"
 3rd user vimrc file: "$VIM\_vimrc"
      user exrc file: "$HOME\_exrc"
  2nd user exrc file: "$VIM\_exrc"
       defaults file: "$VIMRUNTIME\defaults.vim"
       
$ vim $vim/_vimrc【这个好像是系统vimrc配置】
```

## 设置

### 一、vimrc系统设置

```
...
```

### 二、vimrc插件设置

- [Download plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) and put it in the "autoload" directory.

  - `plug.vim`下载到vim目录下面的autoload里面

- 修改Plug安装目录

  - 在vimrc里面修改：`call plug#begin('D:\files\vim\vim-plug') " vim plugin directory(随便放哪里都可以)`

- 修改git代理【下载插件是通过git clone（可能需要代理）】

  ```
  $ git config --global http.proxy http://127.0.0.1:1080
  $ git config --global https.proxy http://127.0.0.1:1080
  ```
  
- 安装插件【安装结束后可以再注释掉git代理：`$vim ~/.gitconfig`】

  ```
  $ vim
  >>>
  esc
  :PlugClean
  :PlugStatus
  :PlugInstall
  :...
  ```

### 三、full vimrc

```
" Settings ##################################################
set nocompatible " no compatiable with old vi
set nobackup
set noswapfile
set nobomb
" @clipboard / registers [ -= -> turn off | += -> turn on ] 
			" $ vim --version 查看是否vim版本支持系统剪切板 [ +clipboard -> support | -clipboard -> unsupport] 
			" "*p -> system clipboard
			" ""p -> vim default register
set clipboard+=unnamed " += 系统剪切板和vim默认寄存器连通 [ "* == "" ]
set mouse-=a
set guioptions-=T
set guioptions-=m
set guioptions-=L
set guioptions-=r
set guioptions-=b
" set lines=45
" set columns=140
" winpos 200 150
set history=1024
set backspace=indent,eol,start whichwrap+=<,>,[,]
set winaltkeys=no
set hlsearch " :set hlsearch ^ :nohl
set number
let $LANG = 'en_US.UTF-8'
set encoding=utf-8
set fileencoding=utf-8
set fileencodings=utf-8,gbk2312,gbk,gb18030,cp936
" @setguifont: set guifont=fontStyle:fontSize
" set guifont=Inconsolata_for_Powerline:h12:cANSI
" set guifont=Consolas:h14
set guifont=Fixedsys:h12
syntax on
" set ruler
" set showcmd
set noeb " remove error sound
set autochdir
set autoindent
" set showmatch " auto hl match () [] ...
set whichwrap=b,s,<,>,[,]
set statusline=%F%m%r%h%w\ [%{&ff}\|%Y]\ [%04l,%04v\|%p%%*%L]
set laststatus=2 " always show status bas
autocmd GUIEnter * simalt ~x
" ################################################## Settings

" Leader ##################################################

" @mapleader should be set first
let mapleader=","
nmap <leader>tt :tabnew<cr>
nmap <leader>tc :tabclose<cr>
nmap <leader>tp :tabprevious<cr>
nmap <leader>tn :tabnext<cr>

" @autocomplete [ ( -> () | [ -> [] | { -> {} ... ]
" inoremap ( ()<ESC>i 
" inoremap [ []<ESC>i
" inoremap { {}<ESC>i
" inoremap " ""<ESC>i
" inoremap ' ''<ESC>i
" ################################################## Leader 

" Kite Plugin ##################################################
let g:kite_auto_complete=1
" ################################################## Kite Plugin

" Vim-Plug Install ##################################################
" @vim-plug: A minimalist Vim plugin manager.

call plug#begin('D:\files\vim82\Vim\vim-plug') " vim plugin directory

" @apperance
Plug 'flazz/vim-colorschemes' " themes
" Plug 'altercation/vim-colors-solarized'
Plug 'vim-airline/vim-airline' " bottom status bar
Plug 'vim-airline/vim-airline-themes'

" @files / motion
Plug 'preservim/nerdtree' " explore files
Plug 'ctrlpvim/ctrlp.vim' " find files
Plug 'tpope/vim-commentary' " comment [ gcc / gc ]
" Plug 'tpope/vim-surround' " [ cs([ ]
" Plug 'preservim/nerdcommenter' " comment 

" @others
" Plug 'python-mode/python-mode', { 'for': 'python', 'branch': 'develop' }
" Plug 'davidhalter/jedi-vim'
" Plug 'tmhedberg/SimpylFold'

call plug#end()
" ################################################## Vim-Plug Install

" Vim-Plug Config ##################################################

" @Plug 'vim-airline/vim-airline-themes
let g:airline_theme='simple'

" @Plug 'preservim/nerdtree'
nmap <leader>e :NERDTreeToggle<cr>

" colorscheme af

" ################################################## Vim-Plug Config


" Change Colorscheme Script ##################################################
" Version 2010-09-12 from http://vim.wikia.com/wiki/VimTip341
" Press key:
"   F8                next scheme
"   Shift-F8          previous scheme
"   Alt-F8            random scheme
" Set the list of color schemes used by the above (default is 'all'):
"   :SetColors all              (all $VIMRUNTIME/colors/*.vim)
"   :SetColors my               (names built into script)
"   :SetColors blue slate ron   (these schemes)
"   :SetColors                  (display current scheme names)
" Set the current color scheme based on time of day:
"   :SetColors now
if v:version < 700 || exists('loaded_setcolors') || &cp
  finish
endif

let loaded_setcolors = 1
let s:mycolors = ['slate', 'torte', 'darkblue', 'delek', 'murphy', 'elflord', 'pablo', 'koehler']  " colorscheme names that we use to set color

" Set list of color scheme names that we will use, except
" argument 'now' actually changes the current color scheme.
function! s:SetColors(args)
  if len(a:args) == 0
    echo 'Current color scheme names:'
    let i = 0
    while i < len(s:mycolors)
      echo '  '.join(map(s:mycolors[i : i+4], 'printf("%-14s", v:val)'))
      let i += 5
    endwhile
  elseif a:args == 'all'
  " ----------------------------------------------------------------------------------------
  " globpath('U:\files\vim\vim-plug\vim-colorschemes\colors', '*.vim') 修改主题colors文件夹路径[vim自带 / 网上下载的]
  " ----------------------------------------------------------------------------------------
    let paths = split(globpath('U:\files\vim\vim-plug\vim-colorschemes\colors', '*.vim'), "\n")
    let s:mycolors = uniq(sort(map(paths, 'fnamemodify(v:val, ":t:r")')))
    echo 'List of colors set from all installed color schemes'
  elseif a:args == 'my'
    let c1 = 'default elflord peachpuff desert256 breeze morning'
    let c2 = 'darkblue gothic aqua earth black_angus relaxedgreen'
    let c3 = 'darkblack freya motus impact less chocolateliquor'
    let s:mycolors = split(c1.' '.c2.' '.c3)
    echo 'List of colors set from built-in names'
  elseif a:args == 'now'
    call s:HourColor()
  else
    let s:mycolors = split(a:args)
    echo 'List of colors set from argument (space-separated names)'
  endif
endfunction

command! -nargs=* SetColors call s:SetColors('<args>')

" Set next/previous/random (how = 1/-1/0) color from our list of colors.
" The 'random' index is actually set from the current time in seconds.
" Global (no 's:') so can easily call from command line.
function! NextColor(how)
  call s:NextColor(a:how, 1)
endfunction

" Helper function for NextColor(), allows echoing of the color name to be
" disabled.
function! s:NextColor(how, echo_color)
  " if len(s:mycolors) == 0
  if 0 == 0
    call s:SetColors('all')
  endif
  if exists('g:colors_name')
    let current = index(s:mycolors, g:colors_name)
  else
    let current = -1
  endif
  let missing = []
  let how = a:how
  for i in range(len(s:mycolors))
    if how == 0
      let current = localtime() % len(s:mycolors)
      let how = 1  " in case random color does not exist
    else
      let current += how
      if !(0 <= current && current < len(s:mycolors))
        let current = (how>0 ? 0 : len(s:mycolors)-1)
      endif
    endif
    try
      execute 'colorscheme '.s:mycolors[current]
      break
    catch /E185:/
      call add(missing, s:mycolors[current])
    endtry
  endfor
  redraw
  if len(missing) > 0
    echo 'Error: colorscheme not found:' join(missing)
  endif
  if (a:echo_color)
    echo g:colors_name
  endif
endfunction

nnoremap <F8> :call NextColor(1)<CR>
nnoremap <S-F8> :call NextColor(-1)<CR>
nnoremap <A-F8> :call NextColor(0)<CR>

" Set color scheme according to current time of day.
function! s:HourColor()
  let hr = str2nr(strftime('%H'))
  if hr <= 3
    let i = 0
  elseif hr <= 7
    let i = 1
  elseif hr <= 14
    let i = 2
  elseif hr <= 18
    let i = 3
  else
    let i = 4
  endif
  let nowcolors = 'elflord morning desert evening pablo'
  execute 'colorscheme '.split(nowcolors)[i]
  redraw
  echo g:colors_name
endfunction
" ################################################## Change Colorscheme Script

```

## 备注

### 随机修改colorscheme脚本

- 修改colorschemes文件夹路径【globpath】【vim自带colors文件夹 / vim-colorschemes插件的colors文件夹 / 。。。】
- f8 / shift +f8 前后切换主题
- alt + f8 随机切换主题

## TODO

### 总结：

- vimrc持续迭代【min / full】
- vim的使用持续学习记录

### 配置的最小化和最大化：

- vimrc【系统设置】【min】
- vimrc【插件设置】【full】

### 不同软件配置：

- gvim / vim cmd【windows】
- vim【linux】
- ideavim
- vscode vim