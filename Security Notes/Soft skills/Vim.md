#### Commands
----
- :ls - show all open files
- :qall - quit all open files
- :edit \<dir-name\> - open netrw explorer
- :find \<file-name\> - search for file name in current directory and open it
- :s/{phrase to replace}/{phrase to replace with}/ - if g at the end replace all in line, if :s% replace in file, if gc at the end replace in file with promp
- :! \<cmd\> - execute external command

#### Keybinds
----
###### Motions
- h - left
- j - down
- k -  up
- l - right
- w - move to beginning of next word
- } - jump to the next paragraph
- $ - go to the end of the line
- x - remove character the cursor is on
- A - append mode
- i - insert mode
- \<ctrl-r\> - redu
- u - undo
- U - undo all changes on a line
- G - jump to end of file
- \<number\>G - jump to line number
- gg - jump to beginning of file
- % - when on a parenthesis it will jump to the other one
- a - open insert mode at the end of the line

###### Operators
- y - yank (copy)
- d - delete text and save to register
- c - delete text, save to register, and start insert mode

##### Tips
- use a motion twice to apply it to the whole line
- motions accept number arguments in front of them

#### .vimrc
----
- Nvim location - ~/.config/nvim/init.vim

#### Custom shit
----
###### Plugins
- telescope - fuzzy finding
	- rebind \<leader\>ff - bring up search
	- rebinf \<leader\>gf - bring up git files search