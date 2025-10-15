# CMDs

## List cmd

```bash
ls --> list files and folders 
-a --> list all files with hidden also
-F --> if there is '/' -> directories , '@' -> shortcut , '*' -> exe "programm"
-aF --> show directories and files 
-l --> long information ( d -> dir , - -> file , l -> link )
-lh --> give long information with easy size reading
-ld --> info for dir itself not what inside it 
-i --> give inode number 
<blabla>* --> it will give all files that ends by "blabla"
```

## Files CMDs

```bash
touch --> make a file 
# if file begins with dot --> hidden file 

cat --> "show file's content"
cat > --> add content to file : to end input press ( crtl+d )
cat << EOF > file --> double input to add it to file # to end inputs write **EOF** 
-n -> show line numbers

more --> if file was big it loads it into more than one screen
head --> give first 10 lines of file
tail --> give last 10 lines of file
-f --> get the live mode of file it is updated currently
cp --> copy file to another file # we can put it in another file or just write the path 
rm --> remove file 
mv --> rename file 
```

## Dir CMDs

```bash
mkdir --> make directory
-R --> give all tree  
# we can use absolute or relative paths
-p --> we use it after mkdir if we want to make a tree directory 
rmdir --> remove directory #for empty dir
rm -r --> remove dir with anything in it 
cp -r --> copy directory with all its content and files
pwd --> print working directory

```

## Dealing with files

### cut cmd

```bash
cut <selected fields> <options> <file>--> get part from file 
-d <sep> --> to select the seperator between fields u want # default is space
-c <range> -> select the range of characters u want
-f <num> -> num of field u want to work on 
# f1 means field1 , f2 means field2
```

### grep cmd ( search in files )

```bash
grep <word> <file>--> search for word include its line  # it will get every existance of this word
-w -> give it as a single word
-i -> ignore case senstive
-c -> "num of word's existance"
-l --> name of file from given files that this word is existing
^<word> --> get lines that this word is first word in line
<word>$ --> get lines that this word is last word in line
-v <word>$ --> "get lines that this word isn't last word in line"
```

### sort cmd

```bash
sort --> sort file alphabetically
-k --> give him key or field which it will be sorted 
-t --> to select the seperator u want # default is space
-n --> to sort by numbers 
-A<num> --> get <num> of lines after the line of this word
```

### Uniq cmd

- Always use `sort` before `uniq` if you want to catch **all duplicates**, not just consecutive ones.

```bash
uniq -> Remove adjacent duplicate lines
-c -> Show number of occurrences for each unique line
-d -> Show only duplicate lines
-u -> Show only unique (non-repeated) lines
-i -> Ignore case when comparing lines

```

### Searching for files in system

```bash
locate --> search for file in system by name 
# good bacause it is so speed 
# bad because if database not updated by root file won't be found

find <dir> <option>--> search live not wait for database to be updated and by anything 
# its cons is being slow 
-name <filename> --> by name 
-size <+,-> n --> by size # n represent 512 bytes and (+,-) higher or lower n 
-type (f,d) --> file or dir
-atime <+,-> n --> Searches for files accessed in the last n days
-user --> Searches for files owned by a specific user
-group --> Searches for files owned by a specific group
```

 

### Archieving

```bash
tar --> archive files
c --> create new tar file # usually we give files .tar to know that is archive 
t --> list table of contents
x --> extract from tar # can give it what files i need to extract , default is all
f --> specify archive device  # default is first media on device
v --> verbose mode # show me archiving process
```

### Compressing

```bash
compress --> compress file # org file is deleted and compressed file " file.Z "
-v --> verbose mode 

uncompress --> to uncompress file

zcat --> to show compressed txt files content without decompressing it 

gzip --> compress file # org file is deleted and compressed file " file.gz "
# if i give him more than file every file will be compressed by its own not together 

gunzip --> decompress .gz files

gzcat --> to show compressed txt files content without decompressing it 

bzip2 --> compress too but better

bunzip2 --> decompress

bzcat --> show txt files without decompress

zip --> compress files with .zip extension and doesn't delete org files
# can give it more than file and will archive and compress them together

unzip --> decompress .zip files 
-l --> show compressed file # not its content ( archive has f1 , f2 not their contents )
```

### Some used cmds

```bash
wc --> {num of lines} {num of words} {num of characters}
-l --> num of lines only
-w --> num of words only
-c --> num of characters only

diff --> differcence between 2 files 
# which line and show the lines have differnce 
# this cmd try to make f1 like f2
# c means change ,, a means appened , d means delete 
# if there is no difference --> no output
```