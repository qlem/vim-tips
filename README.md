# -- vim tips --

## editing file / writing changes / quit
`:w`            write changes  
`:q!`           quit without write changes  
`:wq`           write changes and quit  
`:w file`       write changes in a new file  
`:edit file`    edit file  
`:!cmd`         exec a shell command  

## command auto-completion
`ctrl-D`    list of available cmds according to the beginning of a cmd  
`<tab>`     completion  

## modes
`i`         insert mode  
`v`         visual mode  
`gh`        select mode  
`R`         replace mode  
`gR`        virtual replace mode  
`<esc>`     normale mode  

## navigation
`j`     down  
`k`     up  
`h`     left  
`l`     right  

## scrolling
`ctrl-D`        scroll downward - half of screen  
`ctrl-U`        scroll upward - half of screen  
`ctrl-E`        scroll downward  
`ctrl-Y`        scroll upward  
`zt` `z<CR>`    redraw view - current line at the top of the win  
`zz` `z.`       redraw view - current line at the center of the win  
`zb` `z-`       redraw view - current line at the bottom of the win  
`z+`            redraw view - 1st line below the win to the top of the win  
`z^`            redraw with - 1st line above the win to the bottom of the win  
`zl` `z<right>`     move the view on the text to the right  
`zh` `z<left>`      move the view on the text to the left  
`zL`            move the view on the text half a screenwidth to the right  
`zH`            move the view on the text half a screenwidth to the left  
`zs`            scroll text horizontally to position cursor at start of screen  
`ze`            scroll text horizontally to position cursor at end of screen  

## jumps
`ctrl-O`            go to older cursor position in list  
`ctrl-I` `<tab>`    go to newer cursor position in list  
`g;`                go to older cursor position in change list  
`g,`                go to newer cursor position in change list  
`:ju`               print the jump list  
`:cle`              clear the jump list of the current window  
`:changes`          print the change list  

## insert commands
`a`         append text after the cursor  
`A`         append text at the end of the line  
`i`         insert text before the cursor  
`I`         insert text before the first non-blank in the line  
`gI`        insert text in column 1  
`gi`        insert text in the same position as where insert mode was stopped last time  
`o`         open a new line below the cursor  
`O`         open a new line above the cursor  
`:r file`   insert the content of the file below the cursor  
`:r !cmd`   insert the output of a shell cmd below the cursor  

## insert commands - delete / change
`c`         change text  
`cc`        delete line  
`C`         delete from cursor position to end of the line  
`s`         delete char  
`S`         like `cc`  

## delete / change text
`x` `<del>`     delete char under the cursor  
`X`             delete char before the cursor  
`dd`            delete line  
`D`             delete chars under the cursor until end of line  
`J`             join lines - minimum two lines - insert space  
`gJ`            join lines - minimum two lines - not insert space  
`r{char}`       replace char under the cursor  
`gr{char}`      replace the virtual char under the cursor  
`~`             switch case of the char under cursor and move right  
`g~~`           switch case of current line  
`gUU`           make current line uppercase  
`guu`           make current line lowercase  
`<<` `:[range]< {count}`    shift line leftward  
`>>` `:[range]> {count}`    shift line rightward  

## copying / moving text
`"{a-zA-Z0-9.%#:-"}`    select register  
`:reg`                  list content of all numbered and named registers  
`:reg {arg}`            list content of specified register(s)  
`y`                     yank  
`yy` `Y`                yank line  
`p`                     put text after the cursor  
`P`                     put text before the cursor  
`gp`                    like `p` - leave the cursor just after the new text  
`gP`                    like `P` - leave the cursor just after the new text  
`:[line]pu`             put the text after `[line]` - default current line  
`:[line]pu!`            put the text before `[line]` - default current line  
`]p`                    like `p` - adjust the indent to the current line  
`[P` `]P` `[p`          like `P` - adjust the indent to the current line  

## undo / redo / repeat changes
`u`         undo change  
`U`         undo all latest changes on the last modified line  
`ctrl-R`    redo change which was undone  
`.`         repeat last change  

## search
`/pattern`      search forward  
`/<CR>`         search forward - use the latest used pattern  
`?pattern`      search backward  
`?<CR>`         search backward - use the latest used pattern  
`n`             next match  
`N`             prev match  
`*`             search occurrence forward for the word nearest to the cursor  
`#`             search occurrence backward for the word nearest to the cursor  
`g*`            like `*` - also search for non world  
`g#`            like `#` - also search for non world  
`gd`            go to local declaration  
`gD`            go to global declaration  
`1gd`           like `gd` - ignore matches inside `{}` block that ends before the cursor  
`1gD`           like `gD` - ignore matches inside `{}` block that ends before the cursor  
`ctrl-C`        interrupt current search  

## search and replace
`:s/pattern/string/g`       replace all occurrences in the current line  
`:s/pattern/string/gc`      idem - confirm each subs  
`:%s/pattern/string/gc`     idem - search in the whole file  
`&` `:s` `:&`               repeat last substitute - flags are not remembered  
`:&&`                       repeat last substitute - keep the flags  
`g&`                        repeat last substitute with the same flags with the last search pattern  

## visual mode
`v`         start visual mode  
`V`         start visual mode linewise  
`ctrl-V`    start visual mode blockwise  
`<esc>`     stop visual mode  
`ctrl-G`    switch to select mode  
`gv`        start visual mode with same prev area  
`gn`        search forward last used search pattern (like `n`) and select the match  
`gN`        search backward last used search pattern (like `N`) and select the match  
`o`         move the cursor to the other end of area  
`O`         like `o` - in block mode moves the cursor to the start / end of the current line  

### operating on the visual area
- operators: `~` `d` `c` `y` `>` `<`  
- commands: `r` `s` `C` `S` `R` `x` `D` `X` `Y` `p` `J` `U` `u` `I` `A`  
- objects: *-- see text object selection below --*  

## select mode
`gh`            start select mode characterwise  
`gH`            start select mode linewise  
`g ctrl-H`      start select mode blockwise  
`<esc>`         stop select mode  
`<NL>` `<CR>`   delete selection then enter in insert mode  
`ctrl-O`        switch to visual mode for the duration of one command  
`ctrl-G`        switch to visual mode  

## motions
`operator <number> <motion>` or `operator <number> <object selection>`  

### operators
`c`     change  
`d`     delete  
`y`     yank  
`g~`    switch case  
`gu`    make lowercase  
`gU`    make uppercase  
`<`     shift left  
`>`     shift right  

### horizontal motions
`h`         left  
`l`         right  
`0`         1st char of the line  
`$`         last char of the line  
`^`         1st non-blank char of the line  
`g_`        last non-blank char of the line  
`g0`        1st char of the screen line  
`g^`        1st non-blank char of the screen line  
`g$`        last char of the screen line  
`gm`        half of the screen width to the right - much as possible  
`gM`        half of the text of the line  
`|`         to screen column in current line - default col 0  
`f{char}`   to the occurrence of `{char}` to the right  
`F{char}`   to the occurrence of `{char}` to the left  
`t{char}`   till before occurrence of `{char}` to the right  
`T{char}`   till after occurrence of `{char}` to the left  
`;`         repeat latest `f`, `t`, `F` or `T`  
`,`         repeat latest `f`, `t`, `F` or `T` in opposite direction  

### vertical motions
`k`         up  
`j`         down  
`gk`        up - screen line  
`gj`        down - screen line  
`-`         up - 1st non-blank char  
`+`         down - 1st non-blank char  
`G`         go to line - default last line  
`gg`        go to line - default 1st line  
`H`         go to line from top of window - default 1st line of window  
`M`         go to middle line of window  
`L`         go to line from bottom of window - default last line of window  
`[x]%`      go to `[x]` percentage in the file  

### word motions
`w`     words forward  
`W`     WORDS forward  
`e`     forward to the end of word  
`E`     forward to the end of WORD  
`b`     words backward  
`B`     WORDS backward  
`ge`    backward to the end of word  
`gE`    backward to the end of WORD  

### text object motions
`(`     sentences backward  
`)`     sentences forward  
`{`     paragraphs backward  
`}`     paragraphs forward  
`]]`    sections forward or to the next `{` in the 1st column  
`][`    sections forward or to the next `}` in the 1st column  
`[[`    sections backward or to the previous `{` in the 1st column  
`[]`    sections backward or to the previous `}` in the 1st column  

### various motions
`%`         find the corresponding occurrence for:
- `([{}])`
- `/*` `*/`
- `#if` `#ifdef` `#else` `#elif` `#endif`

`[(`        previous unmatched `(`  
`[{`        previous unmatched `{`  
`])`        next unmatched `)`  
`]}`        next unmatched `}`  
`]m`        next start of a method  
`]M`        next end of a method  
`[m`        previous start of a method  
`[M`        previous end of a method  
`[#`        previous unmatched `#if` or `#else`  
`]#`        next unmatched `#else` or `#endif`  
`[*` `[/`   previous start of a C comment `/*`  
`]*` `]/`   next end of a C comment `*/`  

### text object selection
`aw`            a word  
`iw`            inner word  
`aW`            a WORD  
`iW`            inner WORD  
`as`            a sentence  
`is`            inner sentence  
`ap`            a paragraph  
`ip`            inner paragraph  
`a]` `a[`       a `[]` block  
`i]` `i[`       inner `[]` block  
`a)` `a(` `ab`  a `()` block - including `(` and `)`  
`i)` `i(` `ib`  inner `()` block - excluding the `(` and `)`  
`a}` `a{` `aB`  a `{}` block - including the `{` and `}`  
`i}` `i{` `iB`  inner `{}` block - excluding the `{` and `}`  
`a>` `a<`       a `<>` block - including the `<` and `>`  
`i>` `i<`       inner `<>` block - excluding the `<` and `>`  
`a"` `a'` ``a` ``  a quoted string - including quotes  
`i"` `i'` ``i` ``  a quoted string - excluding quotes  
`at`            a tag block - including `<tag>` and `</tag>`  
`it`            inner tag block - excluding `<tag>` and `</tag>`  

## indenting
`=`     indent operator  
`==`    indent the current line  
`gg=G`  indent the whole file  

## formating text
`:ce [w]`   center lines between specified width columns - default `textwidth` or 80  
`:ri [w]`   right-align lines at specified width columns - default `textwidth` or 80  
`:le [i]`   left-align lines at specified indent - default 0  
*-- see change.txt --*

## sorting text
`:sort /pattern/`       sort lines  
`:sort! /pattern/`      reverse sort lines  
*-- see change.txt --*

## windows

### opening / closing windows
`ctrl-W s`      split current win in two horizontaly  
`ctrl-W v`      split current win in two verticaly  
`ctrl-W n`      create a new empty win horizontaly  
`:vnew`         create a new empty win verticaly  
`ctrl-W q`      quit the current win  
`ctrl-W c`      close the current win  

### selecting windows
`ctrl-W j`      moving cursor to below win  
`ctrl-W k`      moving cursor to above win  
`ctrl-W h`      moving cursor to left win  
`ctrl-W l`      moving cursor to right win  
`ctrl-W w`      move cursor to win below-right  
`ctrl-W W`      move cursor to win above-left  
`ctrl-W t`      move cursor to top-left win  
`ctrl-W b`      move cursor to bottom-right win  
`ctrl-W p`      go to prev win  

### moving windows
`ctrl-W r`      rotate current win downward-rightward  
`ctrl-W R`      rotate current win upward-leftward  
`ctrl-W x`      swap current win with the next one  
`ctrl-W K`      move the current win to the very top - change the window layout  
`ctrl-W J`      move the current win to the very bottom - change the window layout  
`ctrl-W H`      move the current win to the far left - change the window layout  
`ctrl-W L`      move the current win to the far right - change the window layout  
`ctrl-W T`      move the current win to a new tab  

### resizing windows
`ctrl-W =`      make all windows equally high and wide  
`ctrl-W -`      decrease current window height - `:res -[n]`  
`ctrl-W +`      increase current window height - `:res +[n]`  
`ctrl-W _`      set current window height to highest possible - `:res [n]`  
`z{nr}<CR>`     set current window height to `{nr}`  
`ctrl-W <`      decrease current window width  
`ctrl-W >`      increase current window width  
`ctrl-W |`      set current window width to highest possible - `:vertical res [n]`  

## tabs
`:tabnew`       open a new tab  
`:tabn`         move to the next tab  
`:tabp`         move to the prev tab  
`:tabm +[N]`    move the current tab page `[N]` places to the right  
`:tabm -[N]`    move the current tab page `[N]` places to the left  

## buffers
`:ls`           list buffers  
`:buf [buf]`    select specified buffer  

## folding
*TODO*
