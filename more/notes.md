# more
# command format
more [options] file [...]
## 参数
* -num 定义一次显示的行数（specify the number of lines per screenful）
* -d 提示使用者，在画面下方显示 [Press space to continue, 'q' to quit.] ，如果使用者按错键，则会显示 [Press 'h' for instructions.] 而不是 '哔' 声
* -p 不以卷动的方式显示每一页，而是先清除萤幕后再显示内容
* -c 跟 -p 相似，不同的是先显示内容再清除其他旧资料
* -s 当遇到有连续两行以上的空白行，就代换为一行的空白行
* +/pattern 在每个文档显示前搜寻该字串（pattern），然后从该字串之后开始显示
* +num 从第 num 行开始显示
# 常用操作
* <space> -Display next k lines of text [current screen size]
* d -Scroll k lines [current scroll size, initially 11]
* q -Exit from more
* s -Skip forward k lines of text\
* = -Display current line number
* /<regular expression> -Search for kth occurrence of regular expression
* n -
* :n -Go to kth next file
* :p -Go to kth previous file
* :f -Display current file name and line number
* . -Repeat previous command
