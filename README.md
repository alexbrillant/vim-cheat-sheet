# **Vim cheat sheet**

## Move horizontally

| Command | Description
| ------- |:-------------------------------------   |
|`0`        |beginning of line                      |
|`$`        |end of line                            |
|`w W`        |next word or WORD |
|`e E`        |next word or WORD |
|`b B`        |previous word or WORD  |
|`( )`        |beginning of previous or next sentence|
|`{ }`        |beginning of previous or next paragraph|
|`f[char] F[char]`    |next or previous occurence of char after cursor |
|`ta Ta`    |next or previous 'a'                   |
|`; ,`        |repeat `f,F,t,T` in different direction |
|`%`        |jump to matching bracket { } [ ] ( )   |


## Undo redo

`u Ctrl`

## Move cursor

| Command   | Description                        |
| --------- |:-----------------------------------|
|`gg`       |first line                          |
|`G`        |last line                           |
|`nG :n`    |jump to line n                  |
|`nG`       |n'th line of file                   |
|`H`        |top of screen                       |
|`M`        |middle of screen                    |
|`L`        |bottom of screen                    |
|`[[ ]]`        |nex or previous function |
|`Ctrl-O`   |last  cursor position        |
|`Ctrl-I`   |next cursor position  |
|`' '`         |  last cursor position              |
|`g; g,`      |  jump to previous or next edits    |
|`#`          | search word under cursor |
|`g# g*`      | search last or first occurence |
|`g; g,`      |  jump to previous or next edits    |


## Scroll

| Command | Description                        |
| ------- |:-----------------------------------|
|`z.`       |cursor to the center of the screen|
|`zt`       |cursor to the top                 |
|`zb`       |cursor to the bottom              |
|`Ctrl-D`   |  half-page down                  |
|`Ctrl-U`   |  half-page up                    |
|`Ctrl-B`   |  Page up                         |
|`Ctrl-F`   |  Page down                       |
|`Ctrl-Y`   |view pane up                      |
|`Ctrl-E`   |view pane down                    |



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
|`:'a,'b`     |mark a to b to file.txt                           |



## Command mode
| Command     |  Description                                 |
| :-----------|:---------------------------------------------|
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


## Delete 


| Command  | Description                                      |
| :--------| :----------------------------------------------- |
| `D` | Delete till the end of the line |
| `dd` | Delete the whole ine |
| `dt[char]` | Delete till next char |
| `dw` | Delete word |
| `d} d)` | Delete from current to next sentence or paragraph |
| `di{ di( da{ da(` | Delete everything inside or around sentence or paragraph |

## Delete, copy and paste in registe

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`"1p "2p "3p`   | paste the n line deleted                                                 |
|`"add`          | delete it to register a                                                  |
|`"Add`          | delete it to the same register                                           |
|`"Ad`           | delete the entire range and append it to the same register               |
|`"ap "aP`       | paste the line from register a before of after the cursor                |
|`"+p (or "*p)`  | pastes the contents of the clipboard                                     |



## Moving lines

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`:.m 12`        | move current line to after line 12                                    |
|`:5,7m 21`      | move lines 5, 6 and 7 to after line 21                                |
|`:m 'a`         | move current line to after line with mark a                           |
|`:m 'a-1`       | move current line to before line with mark a                          |



## Macros

| Command         | Description                    |
| :-------------  | :------------------------------|
|`qd <commands> q`  |record a macro to register d    |
|`qA <commands> q`           |append to a macro in register A |
|`@d`               |execute macro on register d     |
|`@@`               |execute macro again             |



## View registers

| Command         | Description                                       |
| :-------------  | :-----------------------------------------------  |
|`:reg`             |  view all registers                               |
|`:reg a`           |  view only what you have recorded into register a |
|`qqq`              |  empties register q                               |



## Recursive macros

    qqq qq <commands> @q q record a recursive macro in register q



## Avoiding escape key

    Ctrl-c  escape equivalent



## Vim script

    http://ricostacruz.com/cheatsheets/vimscript.html
