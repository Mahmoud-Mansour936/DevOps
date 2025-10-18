# VI editor

```c
arrows in vi : 'H' ← , 'L' → , 'K' ↑ , 'J' ↓

'i' to go to insert mode and cursor before char
'a' like 'i' but cursor after char
'o' edit mode and new line
'I' beginnig of line 
'A' end of line
'O' new line above cursor  
'w' forward one word 
'b' back one word
'e' end of current word
'nG' go to line n
'G' go to last line 
':n' go to line n //if line is big

'control-B' back one page
'control-F' forward one page
'control-L' refresh screen

's' substitute string for a char at the cursor
'x' delete char at the cursor
'dw' delete word or part of word right of the cursor
'dd' delete line at the cursor
'D' delete all what right of the cursor
'm,nd' delete from line m to line n 
'u' undo

'/string' search forward for string // string is any word
'?string' search backward for string // string is any word
'%s/old/new/g' search for all old and replace ot with new 
// we can remove 'g' to replace first occurance in all lines only

'YY' to copy line
'p' paste under line of the cursor
'P' paste above line of the cursor
'x,y co z' copy lines from x to y and paste under z
'x,y mo z' cut lines from x to y and paste under z

]':w' save without quit
// to save as the project we can enter the name of new project after w
':q!' quit without save
':wq' save and quit
'esc' to return to command mode

'set nu' number the lines , 'set nonu' remove numbers from lines
'set ic' ignore case sensetive , 'set noic' to return it case senstive
'set showmode' to see which mode iam in

 
```