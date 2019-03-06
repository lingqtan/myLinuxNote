## vim hacks ppt 学习笔记

### Features
1. 编辑模式 Mode
四种以上编辑模式：
- Insert Mode `I` `i`
- Normal Mode `<ESC>`
- Visual Mode `V` `v`
- Select Mode
    - 1.1 Normal Mode
        - `h` `j` `k` `l`
        - `f{char}`
        - `$` `0`
        - **`H` 画面最上方 `M` 画面中间行 `L` 画面最下方**
        - **`C` = `c$` change 至行尾**
        - `%` 匹配另一个括号
        - `:h motion.txt`
    - 1.2 Insert Mode
        - `i` `a` `A`
    - 1.3 Visual Mode
        - `v` `V` **`<C-V>`**
2. 语法标记 Syntax Highlight Support
可自订 syntax
3. 编码支援 Encoding
`:set fenc=utf-8 enc=utf-8 tenc=utf-8` 文件编码/内部编码/terminal 编码
4. **快捷键 Key Mapping**
    - `:map` all `:nmap` Normal Mode `:vmap` Visual Mode `:imap` Insert Mode
    - `:nmap <C-c><C-c> :!clang++ -Wall % -o %:r.out<CR>` 用 clang++ 编译正在编辑的文件，输出名为编译文件名.out
    - `:nmap <tab> v>` Normal Mode 也能用 tab 和 shift+tab 缩进
    - `:nmap <s-tab> v<`
    - `:imap <F2> <C-R>=strftime("%c")<CR>` Insert Mode 按下 F2 插入时间戳
5. **文本对象 Text Object**
    - Operator `v | c | d` + Object `a | i` + Region `{ | [ | ( | " | '`
    - 对一个由括号括起来的文本块(Region)进行操作(Operator)，分为 a(包括括号本身)和 i(不包括括号)
    - `va{` 高亮选择由{}括起来的代码块，包括{}括号本身
    - `ci(` change ()里面的内容，不影响()括号
    - `di"` delete ""里面的内容，不影响""
6. 标签栏分页 Tab Pages
    - `:tabnew`
    - `:tabedit path/to/file` 
    - `:help tabpage.txt`
7. 代码折叠 Folds
    - Syntax Fold 以程序语言语法为折叠规则
    - Marker Fold 以特定标记为折叠规则，默认为 `{{{`
    - Indent Fold 以缩拍为折叠规则 `:set foldmethod=indent`
8. ModeLine & FileType
9. **格式化 Formatting**
    - 将格式很乱的代码排版整齐
    - `:set equalprg=perltidy` 选定代码块后 按下 `=` 调用外部程序 perltidy 格式化代码
    - `autocmd Filetype c :set equalprg=indent` 根据文件类型(.c文件)设定 GNU Ident 程序格式化代码
10. QuickFix
    - `:grep [pattern] [filepath]` 调用 grepprg(预设 vimgrep)，并将 grep 结果汇总至 QuickFix
    - `:make` 调用 makeprg(预设 make)执行 makefile，并以该语言的 compiler output parser 汇总结果
    - `:copen` 打开 QuickFix window `:cclose`关闭 `:cnext` `:cprevious`
11. 插件 Plugin