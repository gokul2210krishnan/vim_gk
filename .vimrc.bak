

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
Bundle 'vim-ruby/vim-ruby'
call vundle#end()

" If installed using Homebrew on Apple Silicon
set rtp+=/opt/homebrew/opt/fzf
call plug#begin('~/.vim/plugged')

Plug 'scrooloose/nerdtree'
Plug 'junegunn/fzf.vim'

call plug#end()

" Sets the default vim settings. 
source $VIMRUNTIME/defaults.vim

" Enable syntax highlighting.
syntax on

" Enable set number
set number

" Highlight cursor line underneath the cursor horizontally.
set cursorline

" Set shift width to 4 spaces.
set shiftwidth=4

" Set tab width to 4 columns.
set tabstop=4

" Use space characters instead of tabs.
set expandtab

" Enable auto completion menu after pressing TAB.
set wildmenu

" Make wildmenu behave like similar to Bash completion.
set wildmode=list:longest

" There are certain files that we would never want to edit with Vim.
" Wildmenu will ignore files with these extensions.
set wildignore=*.docx,*.jpg,*.png,*.gif,*.pdf,*.pyc,*.exe,*.flv,*.img,*.xlsx

" Automatically save and load session
" autocmd VimLeave * mksession! ~/.vim/session.vim
" autocmd VimEnter * source ~/.vim/session.vim

nnoremap <leader>f :NERDTreeToggle<CR>:Files<CR>
set ruler
let mapleader = ","
nnoremap <leader>b :Buffers<CR>
nnoremap <leader>f :Files<CR>
nnoremap <leader>z :FZF<CR>
nnoremap <leader>t :NERDTree<CR>
nmap <D-/> i#<Esc>
vmap <D-/> I#<Esc>

function! GetBranchNameOld()
      let branch = system("git rev-parse --abbrev-ref HEAD")
        return branch
endfunction
function! GitBranch()
  let current_file = expand("%:p")
  if stridx(current_file, "such file or directory") >= 0
    return ""
  endif
  let dir = fnamemodify(current_file, ":h")
  let l:root = system("cd " . dir . " && git rev-parse --show-toplevel 2> /dev/null")
  if l:root == ""
    return "[no git repo]"
  endif
  let branch = system("cd " . dir . " && git rev-parse --abbrev-ref HEAD> /dev/null | tr -d '\n'")
  return branch
endfunction
function! GitBranchOld()
  let l:root = system("git rev-parse --show-toplevel 2> /dev/null")
  if l:root == ""
    return "not a git repo"
  endif

  let l:branch = system("git rev-parse --abbrev-ref HEAD 2> /dev/null | tr -d '\n'")
  return l:branch
  " return system("git rev-parse --abbrev-ref HEAD 2>/dev/null | tr -d '\n'")
endfunction

function! StatuslineGit()
  let l:branchname = GitBranch()
  return strlen(l:branchname) > 0?'  '.l:branchname.' ':''
endfunction

"Have a Good Day,\nRemember to check the buffer ( , + b ) before doing anything
set laststatus=2

set statusline=
set statusline+=%#PmenuSel#
set statusline+=%{StatuslineGit()}
set statusline+=%#LineNr#
set statusline+=\ %f
set statusline+=%m\
set statusline+=%=
set statusline+=%#CursorColumn#
set statusline+=\ %y
set statusline+=\ %{&fileencoding?&fileencoding:&encoding}
set statusline+=\[%{&fileformat}\]
set statusline+=\ %p%%
set statusline+=\ %l:%c
set statusline+=\

highlight PmenuSel guifg=white guibg=blue

