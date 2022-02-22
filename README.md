# vim_config4golnag
Are you use vim? Use this config!

## vim
copy and paste this config to ~/.vimrc
```
set hlsearch
set autoindent
set ttyfast
set cindent
set smartindent
set tabstop=4
set shiftwidth=4
set updatetime=300
set number
set ruler
set title
set wrap
set cursorline
set linebreak
set showmatch
set guicursor= "터미네이터 호환
set mouse=r
set laststatus=2
if !has('gui_running')
    set t_Co=256
endif

au BufReadPost *
\ if line("'\"") > 0 && line("'\"") <= line("$") |
\ exe "norm g`\"" |
\ endif

call plug#begin('~/.vim/plugged')

Plug 'fatih/vim-go', { 'do': ':GoUpdateBinaries' }
Plug 'rdnetto/YCM-Generator', { 'branch': 'stable'  }
Plug 'wadackel/vim-dogrun' 	"theme'
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle'  }
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }  "commandline search tool
Plug 'itchyny/lightline.vim'
Plug 'tpope/vim-pathogen'
"Plug 'airblade/vim-gitgutter' "추가,삭제,변경내역 diff check
Plug 'tpope/vim-fugitive' "use git in vim
Plug 'scrooloose/syntastic' "문법 체크
Plug 'Lokaltog/vim-easymotion' "커서이동
Plug 'majutsushi/tagbar'
Plug 'scrooloose/nerdcommenter' "주석
Plug 'edkolev/promptline.vim' "쉘프롬프트
Plug 'terryma/vim-multiple-cursors'
Plug 'jiangmiao/auto-pairs' "짝맞추기
Plug 'vim-scripts/taglist.vim'
Plug 'Yggdroot/indentLine' "들여쓰기 세로줄 라인
Plug 'pangloss/vim-simplefold' "코드접기
Plug 'peterrincker/vim-argumentative' "함수 인자 위치변경
Plug 'andrewradev/sideways.vim' "단어 좌우 이동 ,로 분리된거
Plug 'ycm-core/YouCompleteMe'
Plug 'junegunn/rainbow_parentheses.vim'

call plug#end()

:colorscheme  dogrun
let g:promptline_theme = 'dogrun'
let g:lightline = {
  \ 'colorscheme': 'dogrun',
  \ }

"nerdtree
nmap <F3> :NERDTreeToggle<CR>
noremap <C-h> <C-w>h
noremap <C-j> <C-w>j
noremap <C-k> <C-w>k
noremap <C-l> <C-w>l

" Create default mappings
let g:NERDCreateDefaultMappings = 1
" Add spaces after comment delimiters by default
let g:NERDSpaceDelims = 1
" Use compact syntax for prettified multi-line comments
let g:NERDCompactSexyComs = 1
" Align line-wise comment delimiters flush left instead of following code indentation
let g:NERDDefaultAlign = 'left'
" Set a language to use its alternate delimiters by default
let g:NERDAltDelims_java = 1
" Add your own custom formats or override the defaults
let g:NERDCustomDelimiters = { 'c': { 'left': '/**','right': '*/' } }
" Allow commenting and inverting empty lines (useful when commenting a region)
let g:NERDCommentEmptyLines = 1
" Enable trimming of trailing whitespace when uncommenting
let g:NERDTrimTrailingWhitespace = 1
" Enable NERDCommenterToggle to check all selected lines is commented or not
let g:NERDToggleCheckAllLines = 1

" 'scrooloose/syntastic'
execute pathogen#infect()
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 2
let g:syntastic_auto_loc_list = 2
let g:syntastic_check_on_open = 0
let g:syntastic_check_on_wq = 1


let g:EasyMotion_do_mapping = 0 " Disable default mappings

" Jump to anywhere you want with minimal keystrokes, with just one key binding.
" `s{char}{label}`
nmap s <Plug>(easymotion-overwin-f)
" or
" `s{char}{char}{label}`
" Need one more keystroke, but on average, it may be more comfortable.
nmap s <Plug>(easymotion-overwin-f2)

" Turn on case-insensitive feature
let g:EasyMotion_smartcase = 1

" JK motions: Line motions
map <Leader>j <Plug>(easymotion-j)
map <Leader>k <Plug>(easymotion-k)

"change parameter position
nnoremap <c-a> :SidewaysLeft<cr>
nnoremap <c-s> :SidewaysRight<cr>

"ycm config"
let g:ycm_show_diagnostics_ui = 0
"nnoremap g :YcmCompleter GoTo
"nnoremap d :YcmCompleter GoToDeclaration
"nnoremap t :YcmCompleter GetType
"nnoremap p :YcmCompleter GetParent
let g:ycm_keep_logfiles = 1
let g:ycm_log_level = 'debug'
let g:ycm_confirm_extra_conf = 0
let g:ycm_key_list_select_completion = ['','']
let g:ycm_key_list_previous_completion = ['','']
let g:ycm_autoclose_preview_window_after_completion = 1
let g:ycm_warning_symbol = '>*'

nmap <F4> :TagbarToggle<CR>

augroup rainbow_list
  autocmd!
  autocmd FileType c,cpp,python,go,scheme RainbowParentheses,markdown
augroup END

let g:rainbow#max_level = 16
let g:rainbow#pairs = [['(', ')'], ['{', '}'], ['[', ']']]

" List of colors that you do not want. ANSI code or #RRGGBB
let g:rainbow#blacklist = [233, 234]

filetype plugin indent on
set autowrite
" Go syntax highlighting
let g:go_highlight_fields = 1
let g:go_highlight_functions = 1
let g:go_highlight_function_calls = 1
let g:go_highlight_extra_types = 1
let g:go_highlight_operators = 1

" Auto formatting and importing
let g:go_fmt_autosave = 1
let g:go_fmt_command = "goimports"

" Status line types/signatures
let g:go_auto_type_info = 1
"au filetype go inoremap <buffer> . .<C-x><C-o>
```
