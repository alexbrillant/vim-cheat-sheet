# **Vim cheat sheet**

Cut an arbitraty selection of text : 
```
     d`a y`a
     d}
     d/foo
     d?foo
     "by/foo
     d5}
```

:.,+21g/foo/d means "delete any lines containing the string "foo" from the current one through the next 21 lines"

:.,$v/bar/d means "from here to the end of the file, delete any lines which DON'T contain the string "bar."

:% g/foo/m$ ... and all the "foo" lines will have been moved to the end of the file.

:% g/^   /-1j (for every matching line, go up one line and join them)

:% g/foo/s/bar/zzz/g -- for every line containing "foo" substitute all "bar" with "zzz."

:'a,'bg/foo/j to join any line containing the string foo to its subsequent line, if it lies between the lines between the 'a' and 'b' marks.


## Files

| Command | Description
| ------- |:-------------------------------------   |
|:wq :x         | write and quit|
|:w filename | write a copy of the file you are editing as filename|
|:q!         | quit without saving even if changes were made!|
|:help       | display help|
|`<Tab>`       | use tab completion to scroll through commands that start with what you typed|

## Move horizontally

| Command | Description
| ------- |:-------------------------------------   |
|0 $        |beginning or end of line |
|w W        |next word or WORD |
|I         |edit before the first word on the line |
|A         |edit after the last word on the line |
|e E        |next or previous end of  word or WORD |
|b B        |previous word or WORD  |
|( )        |beginning of previous or next sentence|
|{ }        |beginning of previous or next paragraph|
|f[char] F[char]    |put the cursor at the next or previous occurence of char |
|t[char] T[char]    |put the cursor right before the next or previous char occurence                   |
|; ,        |repeat `f,F,t,T` in different direction |
|%        |jump to matching bracket { } [ ] ( )   |

## Move vertically

| Command   | Description                        |
| --------- |:-----------------------------------|
|gg       |first line                          |
|.       | jump to last modification line |
|G        |last line                           |
|nG :n    |jump to line n                  |
|nG       |n'th line of file                   |
|H M L        |top, middle or low of screen                       |
|[[ ]]        |nex or previous function  |
|Ctrl-O ' '   |last  cursor position        |
|Ctrl-I   |next cursor position  |
|g; g,      |  jump to previous or next edits    |
|#  *        | search word under cursor   |
|g# g*      | search last or first occurence |
|g; g,      |  jump to previous or next edits    |
|gd gD|	local, global definition of symbol under cursor|

## Scroll

| Command | Description                        |
| ------- |:-----------------------------------|
|z. zt zb       |cursor to the center, top or bottom of the screen|
|Ctrl-U Ctrl-D   |  half-page up or down     |
|Ctrl-B Ctrl F   |  Page up or down          |
|Ctrl-Y Ctrl-E   |view pane up or down       |


## Copy and paste

| Command  | Description                                            |
| :-----   |:-----------------------------------------------------  |
|yy      |yank current line (say "first line").                   |
|Y       |yank line from current position to the end              |
|yiw     |yank inner word (copy word under cursor, say "first")   |
|viwp    |select "second", then replace it with what is yanked           |
|Vp      |select current line", then replace it with yanked line.|
| y{number}{h j k l}| yank with movement |


## Substitude

Change enters insert mode after deleting.
Delete stays in normal mode after deleting.

| Command  | Description                                      |
| :--------| :----------------------------------------------- |
|cm|	change text of movement command m|
| D C | delete or change till the end of the line |
| cc S | delete all text on line and start inserting in it's place |
| dnG cnG | delete or change from current position to line n |
| dt[char] ct[char] | delete or change till next char |
| dw cw | delete or change word |
| d} d) c} c) | delete or change from current to next sentence or paragraph |
| di{ di( da{ da( ci{ ci( ca{ ca( | delete or change everything inside or around sentence or paragraph |

## Delete, copy and paste in register

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|"np "ny    | paste or yank the n line deleted        |
|"[register]dd          | delete it to register       |
|"Add          | delete it to the same register       |
|"Ad           | delete the entire range and append it to the same register               |
|"[register]p "[register]P       | paste the line from register a before of after the cursor                |
|"+p (or "*p)  | pastes the contents of the clipboard |

## Moving lines

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|:.m 12        | move current line to after line 12                                    |
|:5,7m 21      | move lines 5, 6 and 7 to after line 21                                |
|:m 'a         | move current line to after line with mark a                           |
|:m 'a-1       | move current line to before line with mark a                          |

## Editing text

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|R| enter replace mode |
|u U     | lowercase or upercase selection|
|guu gUU     | lowercase or upercase line|
|CTRL-A,CTRL-X | increment, decrement next number on same line as the cursor|
|CTRL-W| messed up a word |
|CTRL-U| messed up a line |
|CTRL-O D| delete line in insert mode |
|CTRL-W|	delete word before cursor|
|CTRL-U|	delete all inserted character in current line|
|CTRL-D CTRL-T|	shift left, right one shift width|
|CTRL-A	|insert previously inserted text|
|<m >m|	shift left, right text of movement m|
|n<< n>>|	shift n lines left, right|

## Visual block

| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
|v V ^V	|start/stop highlighting characters, lines, block|
|o	|exchange cursor position with start of highlighting|
|gv	|start highlighting on previous visual area|
|aw as ap	|select a word, a sentence, a paragraph|
|ab aB|	select a block ( ), a block { }|
|shiftj shiftJ     |join lines                               |
|Column + c<char>  |change character in column               |
|YVR<char>         |replace all the line with a repeated char|
|> <                |shift right or left                      |

## Ranges 

| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
|.| The current line |
|$ | last line in the document|
|% |All lines; equivalent to 1,$ |
|7,$ |From the seven line down |
|+2,$-3p | lines starting from two below the current line and up to the third to last line |
|:'a,'b              |mark a to mark b, inclusive                      |

## Search and Replace 

:[range]s/pattern/replacement[/flags...] 

| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
| :%s/pattern/replacement/ |Search pattern on each line, and, if found, replace with replacement |
| :s/hello.*world/***&***/ | you can use the & symbol to put the matching patterns in the replacement string |
| :2,$s/^\(.*\):\(.*\):\(.*\)$/\2 \1 is \3 years old./ |you may group parts of your pattern using \( and \), and then reference them by \1, \2, and so on|

## Global Actions

:[range]g/pattern/command 
     
| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
| :g/^$/d | find all lines with nothing between their start and end and delete them |

## All Purpose Filters 

:range!command

| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
| :3,8!sort | sort lines 3 to 8 |

## Marks 

| Command         | Description                    |
| :-------------  | :------------------------------|
|ma 	|set local file mark a at current cursor location|
|mA |set global mark at current cursor location |
|'a 	|jump to line of mark a (first non-blank character in line)|
|`a 	|jump to position (line and column) of mark a|
|d'a 	|delete from current line to line of mark a|
|d`a 	|delete from current cursor position to position of mark a|
|c'a 	|change text from current line to line of mark a|
|y`a 	|yank text to unnamed buffer from cursor to position of mark a|
|:marks 	|list all the current marks|
|:marks |aB 	list marks a, B|
|m{char}   |create a marker for a letter                      |
|'{char}   |jump to the created marker for a letter           |
|d'{char}  |cut lines from the following location to the mark |
|y'{char}  |yank lines from the following location to the mark|

## Special marks

| Command         | Description                    |
| :-------------  | :------------------------------|
|`.	|jump to position where last change occurred in current buffer|
|`" 	|jump to position where last exited current buffer|
|`0 	|jump to position in last file edited (when exited Vim)|
|`1 	|like `0 but the previous file (also `2 etc)|
|'' 	|jump back (to line in current buffer where jumped from)|
|` ` 	|jump back (to position in current buffer where jumped from)|
|`[ or `] 	|jump to beginning/end of previously changed or yanked text|
|`< or `> 	|jump to beginning/end of last visual selection|

## Normal range 
| Command         | Description                    |
| :-------------  | :------------------------------|
|:'<,'>       |for every line in the visual block(press : while in visual mode)|
|norm         |run in normal mode|
|@a           |the macro recorded in a|

## Undo redo

`u Ctrl`

## Command mode

| Command     |  Description                                 |
| :-----------|:---------------------------------------------|
|:![shell command]          | execute any command in the shell |
|:ny          |copy line number n                            |
|:.tn         |copy at line number n                         |
|:1,5tn+      |copy range of lines first lines after line n  |
|:1,5d        |delete range of lines                         |
|:3,6m.       |move range of lines below cursor              |
|:6t.         |copy line at current line                     |
|:78,83join   |join range of lines together                  |
|:earlier 5s  |go back in time                               |

## Pattern matching commands

| Command  | Description                                                   |
| :------- | :-----------------------------------------------------------  |
|/target ?target         |Search next or previous target |
|n N         |next or previous matching                                                  |
|* #         |next or previous whole word under cursor                                   |

## Search commands

| Command               | Description                                                       |
| :-------------------- | :-----------------------------------------------------------------|
|:/search/d             |search and delete line found                                       |
|`:/search/y             |search and yank line found                                         |
|:/search1/,/search2/d  |search and delete lines with multiple patterns                     |
|:%s/target/\=@0/g      |replace target with what is yanked                                 |
|:g/href/d              |delete all lines with pattern                                      |
|:v/pattern/d           |delete all lines that do not match a pattern.                      |
|:g/lines/z#.3          |display context around pattern.        |
|:g//                   |lines where the last search pattern is                |
|qaq:g/pattern/y A      |copy lines matching pattern to register 'a'.                 |
|:g/pattern/normal @q   |run a macro on matching lines                                      |

## Macros

| Command         | Description                    |
| :-------------  | :------------------------------|
|q[register] <commands> q  |record a macro to register     |
|qA <commands> q           |append to a macro in register A |
|@[register]               |execute macro on register      |
|@@`               |execute macro again             |

## View registers

| Command         | Description                                       |
| :-------------  | :-----------------------------------------------  |
|:reg             |  view all registers                               |
|:reg [register]           |  view only what you have recorded into register  |
|qqq              |  empties register q                               |

## Folding

| Command         | Description                                       |
| :-------------  | :-----------------------------------------------  |
|:set foldmethod=manual|manually define folds|
|zf{motion} {Visual}zf| create a fold. |
|zF| create a fold for [count] lines |
|:{range}fo[ld]| create a fold for {range} |
|zd|delete one fold at the cursor.|
|zD|delete folds recursively |
|zE|eliminate all folds in the window. |
|zo zO|open fold recursively or not|
|zc zC|close one fold under the cursor recursively or not.|
|za zA|open or close recursively or not|
|zv|view cursor line|
|zm zM|fold more: Subtract one from 'foldlevel'.  |
|zr zR|reduce folding: Add one to 'foldlevel'.|
|:{range}foldo[pen][!] |open folds in {range}.  [!] all folds are|
|:{range}foldc[lose][!]|close folds in {range}. [!] all folds |
|zn zN| all folds will be open.|
|zi|invert 'foldenable'.|
|[z ]z|move to the start or the end of the current open fold.|
|zj zk|move downwards or upwards |

## Recursive macros

    qqq qq <commands> @q q record a recursive macro in register q

## Avoiding escape key

    Ctrl-c  escape equivalent

## Vim script

    http://ricostacruz.com/cheatsheets/vimscript.html
