---
title:  Text Manipulation
parent: Linux
nav_order: 11
has_children: false
---

# Manipulating text

# `cat`

Means concatenate

Can be used to print contents of a file
```
cat file
```

Can also be used to concatenate files together like
```bash
cat file1 file2 #puts the content of file2 after the ones from file1 into stdout
cat file1 file2 > newFile #Same as above but saves to a new file (overwrite)
cat file1 file2 >> newFile #Same as above but appends to a file
cat > file #All lines typed will be written in the file until Ctrl+D
cat >> file #Same as above but with append
cat > file << EOF
text
EOF
# Allows to signal a file ending without Ctrl+D
```

> There is an inverse command `tac` which prints the lines in reverse order, but has the same functionalities

# `echo`

Simply displays a string
Can be used to put strings into:
- stdout
- a new file with `>`
- an existing file with `>>`

Using the `-e` flag, allows for characters like newline (`\n`) and tab(`\t`) in the string.

It is widely used to print environment variables (value)

Example:
```bash
echo $USERNAME # Print the value of the env variable
echo hello > newFile #Puts hello into newFile (overwrites)
echo hello >> file # Appends hello to file
```

# Manipulating Large files

- Using `less` is more efficient than an editor (does not try to load everything into memory)
- `head` allows to see only the first n lines
- `tail` allows to see only the last n lines (with `-f` will continuously monitor)

## Viewing compressed files

There are utilities that work directly on compressed files. 

For `gzip` compressed files
    `zcat`, `zless`, `zgrep`, `zdiff`
There are also for the other formats
    `bzcat`, `bzless`
    `xzcat`, `xzless`


# `sed`

- Stream editor
  
- Modifies the content of an input stream (stdin, file, etc)
  
- Data from input is moved to a working space, there all operations/modifications are made and moved to the stdoutor output stream (file, etc.)
  
- When used with the `-e` flag, more than one editing command can be passed

- The `-f` flag allows to pass a scriptfile with sed commands

## Substitution

One big use case is substituting strings
```bash
sed s/pattern/replace_string/ file # Substitutes first occurrence of pattern in every line
sed s/pattern/replace_string/g file #All occurrences of pattern in every line
sed 1,2s/pattern/replace_string/g file #All occurrences in a range of lines 1-3
sed -i s/pattern/replace_string/g file #Rewrites the file with the changes (Not recommended)
```

Delimiting character can be chosen!

# `awk`

- Used to extract and print information from files
- 
- It works well with fields (containing a single piece of data, essentially a column) and records (a collection of fields, essentially a line in a file).
- 
- Also has the `-f` flag to provide a scriptfile with commands
- 
- When dealing with simple fields:
```bash
awk '{ print $0 }' file # Prints the whole file
awk -F: '{ print $1 $7 }' file #Sets the field separator to : and prints the first and seventh fields
```
# File Manipulating

## `sort`

- Allows to sort the lines of a file (based on a key)
- By default sorts alphabetically

Examples:
```bash
sort file #Sorts alphabetically with the first character on each line
cat file1 file2 | sort #Sorts the contents of two files and prints
sort -r file #Sorts in reverse
sort -k 3 file #Sorts by the 3rd field in each line (not the beginning)
sort -u file #SOrts and gets rid of repeated lines (same as sort | uniq)
```

## `uniq`

- Simplifies files by eliminating repeated lines that are consecutive
- Normally used with `sort` first, because of consecutive
- `sort -u` does both in one command

## `paste`
- Used to join files "horizontally"
- It is based on delimiters
- Default delimiter is `\t` but can be changed with the `-d` flag
- Tee `-s` flag allow for serial manner (That is a line per file, separated by delimiters)

Examples:

This files
```bash
Colombia
Argentina
Suiza
Alemania
Italia
Australia
```
```bash
Bogota
Buenos Aires
Berna
Berlin
Roma
Canberra
```

give out the following:
```bash
$ paste file1 file2 -d ":"
Colombia:Bogota
Argentina:Buenos Aires
Suiza:Berna
Alemania:Berlin
Italia:Roma
Australia:Canberra
```
```bash
$ paste file1 file2 -d ":" -s
Colombia:Argentina:Suiza:Alemania:Italia:Australia
Bogota:Buenos Aires:Berna:Berlin:Roma:Canberra
```

## `join`

- Enhanced version of `paste`
- Joins two files that have a common field

## `split`

- Used to split large file into smaller ones
- By default breaks it into files with 1000 lines (changed with the `-l` flag)
- By default creates file with 
    - Prefix: Default is `x`, can be set with `split file some_prefix`
    - Sufix: Default is `aa`, `ab`, etc. With `-d` can be numeric
- Can also split by size (`-b 16` will result in pieces of 16 bytes) or amount of files (`-n`)

# `grep`

- Scan files with matching regex
- Returns lines that match by default

Some examples:
```bash
grep "^some_pattern$" file
grep -v "^some_pattern$" file #Returns line that do not match
grep -C 3 "^some_pattern$" file #Returns 3 lines(before and after) of context and the one that matches
grep -e "^some_pattern$" -e "some_other" file #Multiple patterns
```

> `strings` can be used to extract strings from binaries as well