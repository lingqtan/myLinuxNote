## Vim-misc note

### 在文件中移动
```
20|                 move cursor to column 20.
[[                  Jump to function start
[{                  Jump to block start
```

### 剪切、复制和粘贴
```
/jo[ha]n            Search john or joan
/\<the              Search the, theatre or then
/the\>              Search the or breathe
/\<the\>            Search the
/fred\|joe          Search fred or joe
/\<\d\d\d\d\>       Search exactly 4 digits
:bufdo /searchstr/  Search in all open files
:bufdo %s/aaa/bbb/g Search aaa in all the open buffers and replace it with bbb
:%s/^/hello/g       Replace the begining of each line by hello
:%s/$/Harry/g       Replace the end of each line by Harry
:%s/ *$//g          Delete all white spaces
```

### 和 Unix  系统交互
```
:!pwd               Execute the pwd unix command, then returns to Vi
!!pwd               Execute the pwd unix command and insert output in file
```

### Tabs/Windows 
```
:tab ball           Puts all open files in tabs
:new abc.txt        Edit abc.txt in new window
```

### Indent
```
:set                autoindent Turn on auto-indent
:set smartindent    Turn on intelligent auto-indent
=%                  Indent the code between parenthesis
ggVG=               Indent the whole file
:syntax on          Turn on syntax highlighting
:syntax off         Turn off syntax highlighting
:set syntax=perl    Force syntax highlighting
```

### 窗口
```
:He   全称为 :Hexplore  （在下边分屏浏览目录）
:Ve   全称为 :Vexplore （在左边分屏间浏览目录，要在右边则是 :Ve!）
```
