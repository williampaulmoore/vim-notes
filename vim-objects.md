# Vim Objects 

## Buffers

- An in memory representation of a file that edits are applied to.
- Hidden buffer are loaded but do not have a window.

### Working files:

| File           | Purpose
|----------------|:-------------------------------------------------|
| Backups        | A version of the file before starting to edit    |
| Swap           | Unsaved changes                                  |
| Undo           | An undo tree of the file edits                   |

### Working File settings

| Setting           | Purpose
|-------------------|:----------------------------------------------|
| nobackupfile      | do not create backup files
| backupdir         | location that backup files are created
| noswapfile        | do not create swap files
| directory         | set the location that swap files are created
| noundofile        | do not creaate undo files
| undodir           | set the location that undo files are created

### Buffer commands

| Command           | Action
|-------------------|------------------------------------------------
| ls                | list all buffers
| badd <name>       | add a new buffer
| bdel <name\|num>  | delete the buffer
| b <name\|num>     | show the buffer in the current window
| bn                | show the next buffer in the current window
| b#                | show the alternate buffer in the current window

### Buffer listing

```
:ls
  1  h   "file.md"                      line 1
  2  h   "data.csv"                     line 1
  3 h   "code.rb"                      line 1
  4 %a + "schema.sql"                   line 1
```

| Indicator    |  Meaning 
|--------------|---------------------------------------------------------
| #            | the alternate buffer
| %            | current window's buffer
| h            | buffer is loaded but not visible
| a            | buffer is loaded and visible
| +            | buffer has unsaved edits


## Windows

- A viewport onto a buffer

### Creation commands:

| Command           | Action
|-------------------|--------------------------------------------------------
| new \<filename\>  | Create buffer and window above 
| vnew \<filename\> | Create buffer and window to left
| split             | Create new window on current buffer
| vsplit            | Create new window on current buffer

## Navigation

- There are two type of navigation:
  - Change the current cursor position.
  - Change the current line position within the window.

### Cursor navigation commands

| Command           | Action
|-------------------|--------------------------------------------------------
| h                 | move cursor to the left
| j                 | move cursor down
| k                 | move cursor up
| l                 | move cursor to the right
| 0                 | go to the start of the line
| ^                 | go to the first non white space character
| $                 | go to the end of the line
| g\_               | go to the last non blank character
| e                 | last character of current word
| E                 | last character of the current WORD
| b                 | first character of current word
| B                 | last character of the current WORD
| w                 | first character of the next word
| W                 | first character of the next WORD
| )                 | first character of the next sentence
| (                 | first character of the current sentence
| {                 | first character of the next paragraph marker
| }                 | first character of the current paragraph marker
| G                 | first character of the last line
| gg                | first character of the first line 
| H                 | first character of the first line on the screen.
| M                 | first character of the middle line on the screen.
| L                 | first character of the last line in the screen.
 
_Note_ - A paragraph needs a blank line with no white space.

### Line position on screen navigation commands

| Command           | Action
|-------------------|--------------------------------------------------------
| zz                | center the current line on the screen
| zt                | move the current line to the top of the screen
| zb                | move the current line to the bottom of the screen 


## Registers

- Are a working store for text.
- Some registers have specific purposes while others are general purpose.


| Register  | Name                      | Notes 
|-----------|---------------------------|------------------------------------
| ""        | unnamed register          | yank,paste and delete
| "0-9      | numbered registers        | delete history
| "a-z      | named registers           | general purpose (uppercase to append to)
| "\_       | black hole register       | discard register 
| "%        | active buffer name        |
| ":        | Last command register     | 
| ".        | Last inserted text        |
| "/        | Search pattern register   | Last search pattern
| "\*       | System clipboard buffer   | Content of the system clipboard



### Commands


| Command           | Action
|-------------------|--------------------------------------------------------
| reg               | list the contents of the registers
| let @<reg>=""     | set the contents of a register


## Text objects


| Synonym           | Object
|-------------------|-------------------------------------------------------
| w                 | word by puchtuation
| W                 | word by space
| s                 | sentence 
| p                 | paragraph
| '                 | quotes
| '                 | double quotes
| ],[               | brackets 
| ),(               | parentheses
| >,<               | angle brackets
| },{               | braces
| t                 | tag ( <thml></htm> )


## Modes 

| Mode              | Puropose
|-------------------|-------------------------------------------------------
| Normal            | Generally used for navigation
| Insert            | Allows text to be edited 
| Command           | Allows editing via commands and interaction with the application
| Visual            | Visual edit mode


### Normal -> Insert

| Command           | Action
|-------------------|--------------------------------------------------------
| i                 | Enter insert mode at the cursor
| I                 | Enter insert mode at first non-blank character
| s                 | Delete character under cursor and enter insert mode
| S                 | Delete line and enter insert mode on the line at what was the first character
| a                 | Enter insert mode after the cursor
| A                 | Enter insert mode at the end of the line
| o                 | Add new line below current and enter insert mode on that line
| O                 | Add new line above current and enter insert mode on that line
| C                 | Delete from cursor to end of line and enter insert mode


### Insert -> Normal

| Command           | Action
|-------------------|--------------------------------------------------------
| Esc               | exit Insert mode
| Ctrl+[            | exit Insert mode


### Normal -> Command:


| Command           | Action
|-------------------|--------------------------------------------------------
| :                 | enter command mode if in Normal mode

### Command -> Normal


| Command           | Action
|-------------------|--------------------------------------------------------
| Esc               | exit command mode
