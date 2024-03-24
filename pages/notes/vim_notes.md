# Vim Notes
https://www.freecodecamp.org/news/vim-beginners-guide/

_This article is typed by Vim._

## Four modes:
1. Command Mode: default mode of vim.
2. Command-Line Mode: play around with some commands.
3. Insert Mode: edit contents of a file.
4. Visual Mode: visually select some text and run commands over that section of code.

## Switch between different modes:
* Type `I` on keyboard to switch to Insert Mode. Type `esc` to go back to Command Mode.
* Commands in Command-Line Mode are prefixed with a colon `:`. Type `:` to switch from Command Mode
* Type `v` to switch to Visual Mode from Command Mode.

## Basics
### Enter vim:
`vim` or `vim sample.txt`

### Creat a new file/ Edit an existing file:
`:edit sample.txt`
### Save a file:
`:w`

### Close file and exit vim:
`:q`
### Save the file and close immediately:
`:wq`
### Close the file without saving it:
`:q!`

## Cut, Copy, Paste
1. Place your cursor in the place from where you want to copy the text (being in command mode).
2. Enter Visual mode by pressing the `v` key on the keyboard.
3. Move the cursor to the place where the text you want to copy ends.
> While you move your cursor, Visual mode highlights the text from the beginning up to your cursor.
4. Hit `y` to copy the text or hit `d` to cut the text.
5. Move the cursor to the place where you want to paste the text.
6. Press `p` (in lowercase) to paste the text after the cursor and `P` (in uppercase) to paste the text before the cursor.

## Find and Replace Text
Syntax: `:[range]s/{pattern}/{string}/[flags]`
* `[range]` indicates that you can pass the range of lines. Pass `%` to find and replace in all lines. The range is separated by a comma. To find and replace between lines 5 to 10, pass `5,10`. Use `.` to represent the current line and `$` the last line of the file.
* `{pattern}` indicates the pattern to find the text. You can pass regex patterns here.
* `{string}` is the string to replace in the found text.  
* `[flags]` indicates if you wish to pass any additional flags (for example, the flag `c` is passed to confirm before replacing the text). By default, this does a case-sensitive search. You can change it to do a case-insensitive search by passing a `i` flag.

### Example:
`:%s/Hello/Hi/g`
* `%s` indicates replacing the content in the entire file
* `Hello` is the search text
* `Hi` is the text to replace
* `g` indicates making the change globally
`:2,3s/Hi/Hello and Welcome/gci`
Vim command to change "Hi" with "Hello and Welcome" in 2nd and 3rd line

### Description for each function:
* `y` - Replace the match
* `n` - Skip the match
* `a` - Substitutes the match and all remaining occurrences of the match
* `q` or `Esc` - Quit substitution
* `l` - Replace the match and quit
* `CTRL+Y` - Scroll the screen down
* `CTRL+E` - Scroll the screen up

## Undo or Redo
* To undo a change in Vim, press `u` in command mode.
* To redo, press `CTRL + R`.

* You can prepend a number (n) with u to undo n times.
> For example, `2u` will undo 2 times.
> To list the available undo options, type `:undolist` in command mode.

