## 《Vim 实用技巧》学习笔记

- `.` 重复上次修改 
- `A` = $a 在行尾 append
- `I` = ^i 在 soft 行首 insert
- `C` = c$
- `s` = xi = cl 替换字符
- `f{char}` 查找字符 `;` 查找下一个 `,` 上一个
- `daw` delete a word
- `ga` 查看当前字符的编码

#### Vim 操作符命令
- `c` `d` `y` change/delete/yank
- `g~` `gu` `gU` 切换大小写，`g·` 操作符待决模式
- `>` `<` `=` 缩进/自动缩进
    - `gg=G` 缩进整个文件（从位置 gg 开始，自动缩进(=)至位置 G）

#### 屏幕操作
- `zz` 重绘屏幕，并把当前行显示在窗口正中
    - (Insert Mode)`<C-O>zz` 执行一个 Normal Mode 命令，然后返回 Insert Mode
- `<C-U>`(up) `<C-D>`(down) 翻页(half page)
- `<C-F>`(up) `<C-B>`(down) 翻页(full page)

#### Visual Mode
- `viw` visual 当前 word
- `vit` visually select inside the tag
- `v` `V` `<C-V>` visual 字符/行/列模式
- `gv` 重选上次的 visual 选区
- `o` 切换选区的活动端(首/尾) `~` `U` `u` 切换大小写

#### Ex 命令地址
- `:{start},{end}y` 复制{start}到{end}行
- `:%y` = :1,$y 复制文件所有行
- `1` `$` 文件第一行/最后一行
- `.` `%` 光标所在行/整个文件
- `'<` `'>` visual 选区的起始行/结束行

#### Ex 命令
- (Visual)`:m$` 将 visual 选区移动至文件末尾
- `<C-D>` `<TAB>` 自动补全命令
- `:<C-R><C-W>` 插入当前 word 到命令行
- `:<C-R><C-A>` 插入当前 WORD 到命令行

#### 文件缓冲区
Vim 编辑文件时，编辑的是文件在内存中的映像，也就是"缓冲区"。文件存储在磁盘上，缓冲区存在于内存中。
- `$ vim *.txt` 同时打开多个文件
- `:ls` 查看缓冲区列表 
- `<C-^>` `:bn` `:bp` `:buffer N` 切换缓冲区的文件
- `:bdelete N1 N2 N3` 删除缓冲区
- `:wall` `:qall!` 保存所有文件/不保存且退出所有文件
- `:e!` 回滚保存前的内容

#### 多窗口
**非常有用！！**
- `:sp {file}` 水平切分当前窗口，并在新窗口载入{file}
- `:vsp {file}` 垂直切分当前窗口，并在新窗口载入{file}
- `<C-W><C-W>` `<C-W>{h|j|k|l}` 窗口切换
- `<C-W>c` 关闭当前窗口
- `<C-W>o` 只保留当前窗口，关闭其他
- `<C-W>=` `<C-W>_` `<C-W>|` 使所有窗口等宽高 / 最大化高度 / 最大化宽度
- `[N]<C-W>_` `[N]<C-W>|` 把当前窗口的高度/宽度设为[N]行/[N]列
- `<C-W>{H | J | K | L}` 移动窗口

#### 多标签
标签和窗口的关系：一个标签页可以包含多个窗口
- `:tabedit {file}` 在新标签页中打开{file}
- `<C-W>T` 把当前窗口移动到新标签页
- `:tabclose` `:tabonly` 关闭当前标签页/只保留当前标签页
- `gt` `gT` 切换标签页

#### 文件操作
**非常有用！！**
- `:e %<Tab>` 展开当前文件的完整路径
- `:e %:h<Tab>` :h 会去除文件名，保留路径的其他部分
- `:e.` `:E` 打开文件管理器(netrw)，显示当前工作目录/当前文件所在目录
- `:Sex` `:Vex` 在水平/垂直切分窗口打开文件管理器

#### 文本对象
**非常有用！！**
- `{ d | c | y | v }{i | a}{ w | t | s | p | ( | [ | { | < | " | ' }`
    - i = inside, a = all
    - w = word, t = tag(HTML/XML标签), s = sentence, p = paragraph
    - (), [], {}, <>, "", ''
- `daw` `ciw` 典型应用

#### Motions
- `g{j | k | 0 | ^ | $}` 屏幕行版本的j k 0 ^ $
- `ea` 在 word 结尾 append
- `dt.` 删除到下一个句号前(句号不删除) `t` 功能类似 `f`
- `` \`\` `` 上次跳转动作之前的位置
- `%` 匹配括号间的跳转
- `viwS"` visual 选中 word 然后前后加上"" 需要安装 `surround.vim` 插件
- `cs[{` 将[]括住的内容改成{}括住 需要安装 `surround.vim` 插件

#### 跳转
- `<C-O>` "后退按钮" `<C-I>` "前进按钮"
- `[N]G` = :[N] 跳转到第 N 行
- `H` `M` `L` 跳到屏幕最上方/正中间/最下方
- `gf` = go to file 跳转到光标下的文件名 
- `<C-]>` 跳转到当前 word 的定义之处

#### 正则表达式
- `/\v{pattern}` 用正则表达式查找 `very magic` 模式
- `/\V{pattern}` 不用正则表达式，除了`\`有特殊含义其他为一般字符

#### global 命令
- `:g/{pattern}/[cmd]` 在匹配的行运行 [cmd] Ex 命令 `:g` = `:global`
- `:v/{pattern}/[cmd]` 在**不**匹配的行运行命令 `:v` = `:vglobal`
- `:g/{re}/d` 删除所有匹配行
- `:v/{re}/d` 只保留匹配行
- `:%sort` 对文件所有行排序
- `:g/{start}/ .,{finish} sort` 从{start}开始，到{finish}结束的所有文本行，执行 sort 命令

#### 自动补全
- (Insert)`<C-P>` `<C-N>`
