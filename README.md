# *Vim cheat sheet*

### Move horizontally

| Command | Description
| ------- |:-----------------------------------------------------------------------|
|0        |beginning of line                                                       |
|$        |end of line                                                             |
|fa Fa    |next or previous 'a' after cursor, in the same line (a is any character)|
|ta Ta    |next or previous 'a' (similar to above, but cursor is before a)         |
|;        |repeat same direction                                                   |
|,        |repeat reverse direction                                                |
| %       |jump to matching bracket { } [ ] ( )                                    |


### Move cursor

| Command | Description                                           |
| ------  |:------------------------------------------------------|
|gg       |first line                                             |
|G        |last line                                              |
|nG       |n'th line of file (n is a number; 12G moves to line 12)|
|H        |top of screen                                          |
|M        |middle of screen                                       |
|L        |bottom of screen                                       |


### Cursor scroll

| Command | Description                        |
| ------- |:-----------------------------------|
|z.       |cursor to the center of the screen  |
|zt       |cursor to the top                   |
|zb       |cursor to the bottom                |
|Ctrl-O   |last (older) cursor position        |
|Ctrl-I   |next cursor position (after Ctrl-O) |


### Page scroll

| Command |  Description     |
| ------- |:-----------------|
|Ctrl-D   |  half-page down  |
|Ctrl-U   |  half-page up    |
|Ctrl-B   |  Page up         |
|Ctrl-F   |  Page down       |


### Line scroll

    Ctrl-Y  view pane up

    Ctrl-E  view pane down


### Avoiding escape key

    Ctrl-c  escape equivalent


### Visual block

    shiftj shiftJ     join lines

    Column + c<char>  change character in column

    YVR<char>         replace all the line with a repeated char

### Cursor search

    #            word under cursor

    g# g*        last occurence or first occurence of the word under the cursor


### Jump to previous locations

    ''           last cursor position

    g; g,        jump to previous or next edits


### Default ranges

    :s/old/new/g       current line

    :11,15s/old/new/g  11 to 15 inclusive

    :%s/old/new/g      all lines


### Line ranges

| Command |  Description     | Exemple       |
| ------- |:-----------------|:--------------|
|.        |current line      |:.w single.txt |
|$        |last line         |:$s/old/new/g  |
|1        |first line        |:1s/old/new/g  |
|1,2      |line one to two   |:1,2s/old/new/g|


### Marker ranges

| Command             |  Description                                                |
| ------------------  |:------------------------------------------------------------|
|:'a,'bd              |delete from mark a to mark b, inclusive                      |
|:.,'bd               |delete from the current line to mark b, inclusive            |
|:'a,'bw file.txt     |write from mark a to b to file.txt                           |
|:'a,'bw >> file.txt  |append from mark a to b to file.txt                          |


### Command mode
| Command     |  Description                                 |
| :-----------|:---------------------------------------------|
|:ny          |copy line number n                            |
|:.tn         |copy at line number n                         |
|:1,5tn+      |copy range of lines first lines after line n  |
|:1,5d        |delete range of lines                         |
|:3,6m.       |move range of lines below cursor              |
|:6t.         |copy line at current line                     |
|:78,83join   |join range of lines together                  |
|:earlier 5s  |go back in time                               |


### Pattern matching commands

| Command  | Description                                                   |
| :------- | :-----------------------------------------------------------  |
|n         |next matching                                                  |
|N         |previous matching                                              |
|*         |next whole word under cursor                                   |
|#         |previous whole word under cursor                               |
|g*        |next matching search (not whole word) pattern under cursor     |
|g#        |previous matching search (not whole word) pattern under cursor |


### Search commands

| Command               | Description                                                             |
| :-------------------- | :--------------------------------------------------------------------   |
|:/search/d             |search and delete line found                                             |
|:/search/y             |search and yank line found                                               |
|:/search1/,/search2/d  |search and delete lines with multiple patterns                           |
|:%s/target/\=@0/g      |replace target with what is yanked                                       |
|:g/href/d              |delete all lines with pattern                                            |
|:v/pattern/d           |delete all lines that do not match a pattern.                            |
|:g/lines/z#.3          |display context (5 lines) for all occurrences of a pattern.              |
|:g//                   |list all the lines where the last search pattern is                      |
|qaq:g/pattern/y A      |copy all lines matching a pattern to register 'a'.                       |
|:g/pattern/normal @q   |run a macro on matching lines (example assuming a macro recorded as 'q') |


### Copy and paste

    yy Y  yank current line (say "first line").

    yiw   yank inner word (copy word under cursor, say "first")

    viwp  select "second", then replace it with "first"

    Vp    select "second line", then replace it with "first line".


### Cut and paste without moving

    m{char}   create a marker for a letter

    '{char}   jump to the created marker for a letter

    d'{char}  cut lines from the following location to the mark

    y'{char}  yank lines from the following location to the mark


### Delete, copy and paste in register

| Command      | Description                                                             |
| :------------| :--------------------------------------------------------------------   |
|`"1p "2p "3p`   |paste the n line deleted                                                 |
|`"add`          |delete it to register a                                                  |
|`"Add`          |delete it to the same register                                           |
|`"Ad`           |delete the entire range and append it to the same register               |
|`"ap "aP`       |paste the line from register a before of after the cursor                |
|`"+p (or "*p)`  |pastes the contents of the clipboard                                     |


### Moving lines 

    :.m 12    move current line to after line 12

    :5,7m 21  move lines 5, 6 and 7 to after line 21

    :m 'a     move current line to after line with mark a

    :m 'a-1   move current line to before line with mark a


### Macros

    qd <commands> q  record a macro to register d

    qA...q           append to a macro in register A

    @d               execute macro on register d

    @@               execute macro again


### View registers

    :reg    view all registers

    :reg a  view only what you have recorded into register a

    qqq     empties register q


### Recursive macros

    qqq qq <commands> @q q record a recursive macro in register q


### Vim script

http://ricostacruz.com/cheatsheets/vimscript.html
