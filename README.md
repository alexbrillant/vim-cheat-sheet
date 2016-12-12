# **Vim cheat sheet**

## Files

| Command | Description
| ------- |:-------------------------------------   |
|`:wq :x`         | write and quit|
|`:w filename` | write a copy of the file you are editing as filename|
|`:q!`         | quit without saving even if changes were made!|
|`:help`       | display help|
|`<Tab>`       | use tab completion to scroll through commands that start with what you typed|

## Move horizontally

| Command | Description
| ------- |:-------------------------------------   |
|`0 $`        |beginning or end of line |
|`w W`        |next word or WORD |
|`e E`        |next or previous end of  word or WORD |
|`b B`        |previous word or WORD  |
|`( )`        |beginning of previous or next sentence|
|`{ }`        |beginning of previous or next paragraph|
|`f[char] F[char]`    |next or previous occurence of char after cursor |
|`ta Ta`    |next or previous 'a'                   |
|`; ,`        |repeat `f,F,t,T` in different direction |
|`%`        |jump to matching bracket { } [ ] ( )   |



## Move vertically

| Command   | Description                        |
| --------- |:-----------------------------------|
|`gg`       |first line                          |
|'.       | jump to last modification line |
|`G`        |last line                           |
|`nG :n`    |jump to line n                  |
|`nG`       |n'th line of file                   |
|`H M L`        |top, middle or low of screen                       |
|`[[ ]]`        |nex or previous function |
|`Ctrl-O ' '`   |last  cursor position        |
|`Ctrl-I`   |next cursor position  |
|`g; g,`      |  jump to previous or next edits    |
|`#`          | search word under cursor |
|`g# g*`      | search last or first occurence |
|`g; g,`      |  jump to previous or next edits    |


## Scroll

| Command | Description                        |
| ------- |:-----------------------------------|
|`z. zt zb`       |cursor to the center, top or bottom of the screen|
|`Ctrl-U Ctrl-D`   |  half-page up or down     |
|`Ctrl-B Ctrl F`   |  Page up or down          |
|`Ctrl-Y Ctrl-E`   |view pane up or down       |



## Visual block

| Command          |  Description                            |
| ---------------- |:--------------------------------------  |
|`shiftj shiftJ`     |join lines                               |
|`Column + c<char>`  |change character in column               |
|`YVR<char>`         |replace all the line with a repeated char|
|`> <`                |shift right or left                      |



## Ranges

| Command           |  Description     |
| ----------------  |:-----------------|
|`:s/old/new/g`       |current line      |
|`:11,15s/old/new/g`  |11 to 15 inclusive|
|`:%s/old/new/g`      |all lines         |
|`.`        |current line      |:.w single.txt |
|`+n -n [n(1 by default)]`        |n line after or before current line      |:.w single.txt |
|`1 $`        |first line and last line         |:$s/old/new/g  |
|`1,2`      |line one to two   |:1,2s/old/new/g|
|`:'a,'b`              |mark a to mark b, inclusive                      |
|`:.,'b`               |current line to mark b, inclusive            |
|`:'a,'b`     |mark a to b to |


## Undo redo

`u Ctrl`

## Command mode
| Command     |  Description                                 |
| :-----------|:---------------------------------------------|
|`:![shell command]`          | execute any command in the shell |
|`:ny`          |copy line number n                            |
|`:.tn`         |copy at line number n                         |
|`:1,5tn+`      |copy range of lines first lines after line n  |
|`:1,5d`        |delete range of lines                         |
|`:3,6m.`       |move range of lines below cursor              |
|`:6t.`         |copy line at current line                     |
|`:78,83join`   |join range of lines together                  |
|`:earlier 5s`  |go back in time                               |



## Pattern matching commands

| Command  | Description                                                   |
| :------- | :-----------------------------------------------------------  |
|`/target ?target`         |Search next or previous target |
|`n N`         |next or previous matching                                                  |
|`* #`         |next or previous whole word under cursor                                   |



## Search commands

| Command               | Description                                                       |
| :-------------------- | :-----------------------------------------------------------------|
|`:/search/d`             |search and delete line found                                       |
|`:/search/y`             |search and yank line found                                         |
|`:/search1/,/search2/d`  |search and delete lines with multiple patterns                     |
|`:%s/target/\=@0/g`      |replace target with what is yanked                                 |
|`:g/href/d`              |delete all lines with pattern                                      |
|`:v/pattern/d`           |delete all lines that do not match a pattern.                      |
|`:g/lines/z#.3`          |display context around pattern.        |
|`:g//`                   |lines where the last search pattern is                |
|`qaq:g/pattern/y A`      |copy lines matching pattern to register 'a'.                 |
|`:g/pattern/normal @q`   |run a macro on matching lines                                      |



## Copy and paste

| Command  | Description                                            |
| :-----   |:-----------------------------------------------------  |
|`yy`      |yank current line (say "first line").                   |
|`Y`       |yank line from current position to the end              |
|`yiw`     |yank inner word (copy word under cursor, say "first")   |
|`viwp`    |select "second", then replace it with "first"           |
|`Vp`      |select "second line", then replace it with "first line".|



## Cut and paste without moving

| Command  | Description                                      |
| :--------| :----------------------------------------------- |
|`m{char}`   |create a marker for a letter                      |
|`'{char}`   |jump to the created marker for a letter           |
|`d'{char}`  |cut lines from the following location to the mark |
|`y'{char}`  |yank lines from the following location to the mark|

## Delete and change

Change enters insert mode after deleting.
Delete stays in normal mode after deleting.

| Command  | Description                                      |
| :--------| :----------------------------------------------- |
| `D C` | Delete till the end of the line |
| `dd cc` | Delete the whole ine |
| `dnG cnG` | Delete from current position to line n |
| `dt[char] ct[char]` | Delete till next char |
| `dw cw` | Delete word |
| `d} d) c} c)` | Delete from current to next sentence or paragraph |
| `di{ di( da{ da( ci{ ci( ca{ ca(` | Delete everything inside or around sentence or paragraph |

## Delete, copy and paste in registe

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`"np "ny `   | paste or yank the n line deleted        |
|`"[register]dd`          | delete it to register       |
|`"Add`          | delete it to the same register       |
|`"Ad`           | delete the entire range and append it to the same register               |
|`"[register]p "[register]P`       | paste the line from register a before of after the cursor                |
|`"+p (or "*p)`  | pastes the contents of the clipboard |



## Moving lines

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`:.m 12`        | move current line to after line 12                                    |
|`:5,7m 21`      | move lines 5, 6 and 7 to after line 21                                |
|`:m 'a`         | move current line to after line with mark a                           |
|`:m 'a-1`       | move current line to before line with mark a                          |

## Editing text

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`u U`     | lowercase or upercase selection|
|`guu gUU`     | lowercase or upercase line|
|`CTRL-A,CTRL-X` | increment, decrement next number on same line as the cursor|
|`CTRL-W`| messed up a word |
|`CTRL-U`| messed up a line |
|`CTRL-O D`| delete line in insert mode |



## Macros

| Command         | Description                    |
| :-------------  | :------------------------------|
|`q[register] <commands> q`  |record a macro to register     |
|`qA <commands> q`           |append to a macro in register A |
|`@[register]`               |execute macro on register      |
|`@@`               |execute macro again             |



## View registers

| Command         | Description                                       |
| :-------------  | :-----------------------------------------------  |
|`:reg`             |  view all registers                               |
|`:reg [register]`           |  view only what you have recorded into register  |
|`qqq`              |  empties register q                               |

## Folding


| Command         | Description                                       |
| :-------------  | :-----------------------------------------------  |
|`:set foldmethod=manual`|manually define folds|
|`zf{motion} {Visual}zf`| create a fold. |
|`zF`| create a fold for [count] lines |
|`:{range}fo[ld]`| create a fold for {range} |
|`zd`|delete one fold at the cursor.|
|`zD`|delete folds recursively |
|`zE`|eliminate all folds in the window. |
|`zo zO`|open fold recursively or not|
|`zc zC`|close one fold under the cursor recursively or not.|
|`za zA`|open or close recursively or not|
|`zv`|view cursor line|
|`zm zM`|fold more: Subtract one from 'foldlevel'.  |
|`zr zR`|reduce folding: Add one to 'foldlevel'.|
|`:{range}foldo[pen][!]` |open folds in {range}.  [!] all folds are|
|`:{range}foldc[lose][!]`|close folds in {range}. [!] all folds |
|`zn zN`| all folds will be open.|
|`zi`|invert 'foldenable'.|
|`[z ]z`|move to the start or the end of the current open fold.|
|`zj zk`|move downwards or upwards |



## Recursive macros

    qqq qq <commands> @q q record a recursive macro in register q



## Avoiding escape key

    Ctrl-c  escape equivalent



## Vim script

    http://ricostacruz.com/cheatsheets/vimscript.html
