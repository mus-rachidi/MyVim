# Vim Customization Guide

This guide explains how to use the features configured in the `.vimrc` file to enhance your Vim experience.

---

## Installation

1. **Install Vim-Plug** (if not already installed):
   The `.vimrc` automatically downloads Vim-Plug. Launch Vim, and if prompted, plugins will install automatically.

2. **Install Plugins**:
   Open Vim and run:
   ```vim
   :PlugInstall
   ```

---

## Features and How to Use Them

### 1. **Line Numbers**
   - **Relative Numbers**: Displays relative line numbers to your current position for easier navigation.
   - **Command**: Toggle line numbers with:
     ```vim
     :set number
     :set relativenumber
     ```

### 2. **Color Scheme**
   - **Dracula Theme**:
     A dark color scheme for better aesthetics and reduced eye strain.
   - Automatically applied if the `dracula` plugin is installed.

### 3. **NERDTree**
   - **File Explorer**: Open/close the tree view with:
     ```vim
     <Ctrl-n>
     ```
   - **Show Hidden Files**: Enabled by default.

### 4. **Airline**
   - **Status Bar**: Displays useful information like the current mode, file position, and branch.
   - Custom Theme: Dracula.

### 5. **FZF (Fuzzy Finder)**
   - **File Search**: Launch with:
     ```vim
     <Ctrl-p>
     ```
   - **Requirements**: Ensure `fzf` is installed on your system.

### 6. **Git Integration (Fugitive)**
   - Run Git commands directly within Vim:
     ```vim
     :Git status
     :Git commit
     ```

### 7. **IndentLine**
   - Displays vertical lines to indicate indentation levels.
   - Toggle with:
     ```vim
     :IndentLinesToggle
     ```

### 8. **Auto-Pairs**
   - Automatically closes brackets and quotes as you type.
   - Example: Typing `(` automatically adds `)`.

### 9. **Commenting (NERDCommenter)**
   - Toggle comments with:
     ```vim
     <Leader>c<space>
     ```

### 10. **Linting and Fixing (ALE)**
   - **Linting**: Automatically checks for syntax and style errors in Python and JavaScript.
   - **Fix on Save**: Auto-fixes issues on save.
   - Configure linters and fixers in `.vimrc`.

### 11. **Key Mappings**
   - Clear search highlights:
     ```vim
     <Space>
     ```
   - Save file:
     ```vim
     <Ctrl-s>
     ```

---

## Miscellaneous Settings

1. **Splits**:
   - New splits open below or to the right by default.
2. **Clipboard**:
   - Uses the system clipboard for copy-paste.
3. **Search**:
   - Case-insensitive unless uppercase letters are used.

---
Enjoy your enhanced Vim setup!

```bash
" Automatically install vim-plug if not already installed
if empty(glob('~/.vim/autoload/plug.vim'))
  silent !curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
  autocmd VimEnter * PlugInstall
endif

" Load vim-plug for managing plugins
call plug#begin('~/.vim/plugged')

" Plugins for features and colors
Plug 'dracula/vim', { 'as': 'dracula' }
Plug 'preservim/nerdtree'          " File explorer
Plug 'vim-airline/vim-airline'    " Status bar
Plug 'vim-airline/vim-airline-themes' " Airline themes
Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }  " Fuzzy search
Plug 'junegunn/fzf.vim'
Plug 'tpope/vim-fugitive'         " Git integration
Plug 'Yggdroot/indentLine'        " Show indent lines
Plug 'jiangmiao/auto-pairs'       " Auto close brackets/quotes
Plug 'scrooloose/nerdcommenter'   " Easy commenting
Plug 'dense-analysis/ale'         " Linting and syntax checking

call plug#end()

" General settings
set number                " Show line numbers
set relativenumber        " Relative line numbers
set showcmd               " Show command in bottom bar
set cursorline            " Highlight current line
set expandtab             " Use spaces instead of tabs
set tabstop=4             " Tab width (visual)
set shiftwidth=4          " Tab width (indentation)
set softtabstop=4         " Tab width (editing)
set autoindent            " Enable auto-indentation
set smartindent           " Smarter indentation
set wrap                  " Enable line wrapping
set ignorecase            " Case insensitive search
set smartcase             " Case sensitive if uppercase is present
set wildmenu              " Enable command menu
set wildmode=list:longest
set clipboard=unnamedplus " Use system clipboard

" Color scheme
syntax on
colorscheme dracula
set background=dark

" Airline configuration
let g:airline#extensions#tabline#enabled = 1
let g:airline_theme='dracula'

" NERDTree settings
map <C-n> :NERDTreeToggle<CR>
let NERDTreeShowHidden=1

" FZF keybindings
nnoremap <C-p> :Files<CR>

" IndentLine settings
let g:indentLine_enabled = 1

" ALE settings
let g:ale_linters = {
\   'python': ['flake8'],
\   'javascript': ['eslint'],
\}
let g:ale_fix_on_save = 1
let g:ale_fixers = {
\   '*': ['remove_trailing_lines', 'trim_whitespace'],
\   'javascript': ['prettier'],
\   'python': ['black'],
\}

" NERDCommenter settings
let g:NERDCreateDefaultMappings = 1

" Miscellaneous settings
set splitbelow            " Horizontal splits open below
set splitright            " Vertical splits open right
set updatetime=300        " Faster update time for plugins
set timeoutlen=500        " Faster key mappings

" Key mappings
nnoremap <Space> :noh<CR> " Clear search highlights
nnoremap <C-s> :w<CR>     " Save file
```
