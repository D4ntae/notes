#### Commands
----
- :ls - show all open files
- :qall - quit all open files
- :edit \<dir-name\> - open netrw explorer
- :find \<file-name\> - search for file name in current directory and open it
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