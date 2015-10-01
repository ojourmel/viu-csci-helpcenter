### Vim Configuration for VIU CSCI

[Vim](http://www.vim.org/) is an open source command line text editor.
It is very useful for editing files over an`ssh` shell.

There are, however, several configuration changes that can be made to help make things easier to read, program, and mark.

These are made through the `vimrc` file. A simple one is availible here.

1. Open an new file, in your home directory, called `.vimrc`
   Notice the **.** in the file name
   
2. Copy in this new file, the following text:
````
" Gotta be first
set nocompatible

filetype off

" --- General settings ---
set ruler
set number
set showcmd
set incsearch
set hlsearch

syntax on

set mouse=a

" Show partial commands in the last line of the screen
set showcmd

" Highlight searches (use <C-L> to temporarily turn off highlighting; see the
" mapping of <C-L> below)
set hlsearch

" Use case insensitive search, except when using capital letters
set ignorecase
set smartcase

" Allow backspacing over auto indent, line breaks and start of insert action
set backspace=indent,eol,start

" When opening a new line and no file type-specific indenting is enabled,
" keep the same indent as the line you're currently on. Useful for READE, etc.
set autoindent

" Stop certain movements from always going to the first character of a line.
" While this behaviour deviates from that of Vi, it does what most users
" coming from other editors would expect.
set nostartofline

" Instead of failing a command because of unsaved changes, instead raise a
" dialogue asking if you wish to save changed files.
set confirm

" Indentation settings for using 2 spaces instead of tabs.
" Do not change 'tabstop' from its default value of 8 with this setup.
set shiftwidth=3
set tabstop=3
set expandtab

map <F1> <Esc>
imap <F1> <Esc>

filetype on
syntax on

````
3. Save, close, and reopen any instances of `vim` you have open

4. If you ever want to remove this, simply run: `rm ~/.vimrc`
