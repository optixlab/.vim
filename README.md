# .vim
Reference: http://mirnazim.org/writings/vim-plugins-i-use/
vim for Windows & Linux (needs .vimrc)


OLD WAY OF DOING THINGS

  * git push origin master
	
	Submodules:
  1. git submodule add git://github.com/tpope/vim-fugitive.git bundle/fugitive
  2. git submodule add git://github.com/Raimondi/delimitMate.git bundle/delmitmate
  3. git submodule add git://github.com/vim-airline/vim-airline-themes.git bundle/vim-airline-themes/
  4. git submodule add git://github.com/jalvesaq/Nvim-R bundle/Nvim-R/
  5. git submodule add https://github.com/ConradIrwin/vim-bracketed-paste bundle/vim-bracketed-paste

	Run init and update commands after every submodule command. 
  - git submodule init && git submodule update

	If you need to make changes to submodule:
  - git ls-files
  - git rm --cached colors/vim-blackboard

Usage of various plugins:
 1. [Fugitive readme](https://github.com/tpope/vim-fugitive/blob/master/README.markdown)
 		- Git wrapper. View any blob, tree, commit, or tag in the repository with `:Gedit` (and
		`:Gsplit`, `:Gvsplit`, `:Gtabedit`, ...).  Edit a file in the index and
		write to it to stage the changes.  Use `:Gdiff` to bring up the staged
		version of the file side by side with the working tree version and use
		Vim's diff handling capabilities to stage a subset of the file's
		changes.

		Bring up the output of `git status` with `:Gstatus`.  Press `-` to
		`add`/`reset` a file's changes, or `p` to `add`/`reset` `--patch`.  And guess
		what `:Gcommit` does!

 2. [DelimitMate readme](https://github.com/Raimondi/delimitMate/blob/master/README.md): 
 		- Intelligent autocompletion for quotes, parenthesis, brackets etc.
 3. [Airline Theme readme](https://github.com/vim-airline/vim-airline-themes/blob/master/README.md):
  	- Once installed, use :AirlineTheme <theme> to set the theme, e.g. :AirlineTheme simple
		- To set in .vimrc, use let g:airline_theme='<theme>', e.g. let g:airline_theme='simple'
		- Note: The command :AirlineTheme is only available, if you have also cloned and installed the main vim-airline repository.
 4. []():
 5. whenever you are in the *insert mode* and paste into your terminal emulator using `command+v`, `shift+insert`, `ctrl+shift+v` or `middle-click`, vim will automatically `:set paste` for you.

Vundle
[REFERENCE for Vundle](

# This is how you set it up on Windows

Basics: 

- `vim --version | grep vimrc` to get file locations 
- In VIM: `echo $VIM` etc. to get the pathnames
- $VIM => c:\Program Files (x86)\Git\share\vim
- readme file is under ~/.vim/README.md
- I got everything running like it would on Linux but it wouldn't work
- Turns out, need to modify not ~/.vimrc and add pathogen to .vim/*
- Rather, modify user vimrc in $VIM/vimrc

Windows:
This is the link to use: [Git Bash Vim setup](https://github.com/VundleVim/Vundle.vim/wiki/Vundle-for-Windows)

Needs cURL to run Vundle ([better](https://lepture.com/en/2012/vundle-vs-pathogen) version of Pathogen -

Original VIM way  Pathogen Way
================  ================
vim/              vim/bundle/
    syntax/           html/
        html.vim          syntax/
    indent/                   html.vim
        html.vim          indent/
                              html.vim 



This allows you to take `html` as a bundled app. 

```{sh}
set nocompatible               " be iMproved
filetype off                   " required!

set rtp+=~/.vim/bundle/vundle/
call vundle#rc()

" let Vundle manage Vundle
" required! 
Bundle 'gmarik/vundle'

" My Bundles here:
"
" original repos on github
Bundle 'tpope/vim-fugitive'
Bundle 'Lokaltog/vim-easymotion'
Bundle 'rstacruz/sparkup', {'rtp': 'vim/'}
Bundle 'tpope/vim-rails.git'
" vim-scripts repos
Bundle 'L9'
Bundle 'FuzzyFinder'
" non github repos
Bundle 'git://git.wincent.com/command-t.git'
```

https://github.com/VundleVim/Vundle.vim/wiki/Vundle-for-Windows#vundle-on-windows
