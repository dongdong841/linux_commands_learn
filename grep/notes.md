# grep
grep(global regular expression print，全局正则表达式及打印)工具是在一个或多个文件中搜索是否包含某给定字符串。
此工具只显示包含查找字符串的文件行，并不修改搜索出的文件。
# command format
> grep [options] pattern [file-list]
## 参数说明
### 参数
pattern为正则表达式，即要搜索的内容。

file-list为grep要搜索的普通文件的路径名列表。
### 选项
#### 主选项
必须带下面3个选项中的一个，默认带-G。
* -E 将pattern解释为可扩展的正则表达式。（不懂......）
* -F 将pattern解释为固定的字符串。
* -G 将pattern解释为基本的正则表达式。（不带任何选项时默认为此选项）
#### 其他选项
* --count -c 只显示每个文件中包含匹配的行的数目
* --context=n -C n 对每个匹配的行显示n行上下文
* --file=file -f file 读取文件file，该文件的每行都包含一个pattern，从输入中查找匹配每个模式的行（注意：文件file中的每行pattern不能带单引号）
* --no-filename -h 当搜索多个文件时，在每行的开始不显示文件名
* --ignore-case -i 忽略pattern中的大小写
*
