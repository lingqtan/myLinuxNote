##vimtutor 学习笔记##
- `vimtutor<ENTER>`

###MOTIONS###
- `j` `k` `h` `l` 光标移动
- `w` `e` 单词移动
    - `2e` `3w` 移动2/3个单词
- `$` 移动至行尾
- `0` 移动至行首
- `G` 移动至文件末尾
- `gg` 移动至文件起始
- `100G` 移动至行号100
- `<C-O>` `<C-I>` 跳转至上一次/下一次位置
- `%` 移动至括号匹配的另一个括号

###OPERATORS###
- `d` = delete 删除
    - `dw` 删除一个 word
    - `d$` 删除一行 (光标开始)
    - `d2w` 删除2个 word
    - `dd` 删除一行
    - `2dd` 删除2行 
- `c` = change 修改
    - `ce` 修改一个 word
    - `c$` 修改一行(光标开始)
- `y` = yank(= copy) 复制
    - `yy` 复制一行
    - `yw` 复制一个 word

###MODES###
- `<ESC>` 切换到 Normal Mode
- `i` `a` `o` `O` `A` 切换到 Insert Mode
- `v` 切换到 Visual Mode
    - `v` -> (高亮选择段落) -> `:w FILE2.txt` 将选择段落另存为FILE2.txt
    - `v` -> (高亮选择段落) -> `d` 将选择段落删除
- `R` 切换到 Replace Mode 

###COMMANDS###
- `:q!` 不保存直接退出
- `:w = write` 保存文件
    - `:w FILE2.txt` 另存为FILE2.txt
- `:r` = retrieve 插入
    - `:r FILE2.txt` 将文件内容插入到下一行 
    - `:r !ls` 将 shell 命令的输出插入到下一行
- `:e` = edit 打开文件
    - `:e FILE2.txt` 
    - `:e ~/.vimrc` -> `:r $VIMRUNTIME/vimrc_example.vim` 将官方示例插入到 .vimrc
- `:!ls` 不退出 vim 执行 shell 命令
:set OPTION 配置 vim
    - `:set ic` 搜索时ignore case
    - `:set hls is` 设置 highlight search 和 incsearch(增量搜索)
    - `:set no[OPTION]` 取消设置[OPTION]
- `:help` 打开帮助
    - `:help w` 查看 w 命令帮助
    - `:help user-manual` 查看帮助手册
    - `:help .`
- `<C-D>` `<TAB>` 命令补全(:开头的命令)

- `u` = undo 撤销
- `U` 撤销一行所有修改
- `<C-R>` = redo 恢复
- `<C-G>` 显示file/cursor info
- `x` 删除一个字符
- `p` = put(= paste) 把删除的内容粘贴
- `r` = replace 替换一个字符
- `:s` = substitute 替换
    - `:s/old/new`     替换一行内的 old 为 new(只替换一次)
    - `:s/old/new/g`   替换一行内的 old 为 new(替换所有)
    - `:%s/old/new/g`  替换文件内的 old 为 new
    - `:%s/old/new/gc` 替换文件内的 old 为 new，且每次弹出 prompt 提示是否替换

###FIND###
- `/` `?` 搜索
    - `/xxx\c` 搜索 xxx 且 ignore case
- `n` `N` = next 找到下一个/上一个
