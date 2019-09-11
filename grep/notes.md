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
* -A n 对每个匹配的行显示n行下文
* -B n 对每个匹配的行显示n行上文
* --file=file -f file 读取文件file，该文件的每行都包含一个pattern，从输入中查找匹配每个模式的行（注意：文件file中的每行pattern不能带单引号）
* --no-filename -h 当搜索多个文件时，在每行的开始不显示文件名
* --ignore-case -i 忽略pattern中的大小写
* --files-with_matches -l 仅显示匹配的文件名
* --max-count=n -m n显示包含匹配的n行后停止搜索匹配
* --line-number -n 在显示的每行前显示行号
* --quiet -q 不显示匹配到的行，仅设置退出码（退出码：0 匹配成功， 1 没匹配到， 2 文件错误）
* --recursive -r 递归搜索文件夹
* --invert-match -v 显示不包含匹配的行
* --word-regexp -w 使用该选项，pattern必须与整个字匹配
* --line-regexp -x pattern匹配整行
* --color=auto 被搜索到的行在显示时关键字带颜色显示
# 正则表达式
|表达式|描述|
|-|-|
|^|'^grep'匹配所有以grep开头的行|
|$|'grep$'匹配所有以grep结尾的行|
|.|匹配任意一个非换行符的字符，例如：'gr.p'匹配gr后接一个任意字符，然后是p|
|*|匹配一个或多个先前字符|
|.*|任意字符|
|[]|匹配一个指定范围内的字符，例如：'[Gg]rep'匹配Grep和grep|
|[^]|与[]相反，例如：'[A-FH-Z]rep'匹配不包含A-F和H-Z的一个字母开头，后面紧跟rep的行|
|<|如:'<grep'匹配包含以grep开头的单词的行|
|>|如'grep>'匹配包含以grep结尾的单词的行|
|x{m}|重复字符x，m次，如：'0{5}'匹配包含5个o的行|
|x{m,}|重复字符x,至少m次，如：'o{5,}'匹配至少有5个o的行|
|x{m,n}|重复字符x，至少m次，不多于n次，如：'o{5,10}'匹配5--10个o的行|
|\w|匹配文字和数字字符，也就是[A-Za-z0-9]，如：'G\w*p'匹配以G后跟零个或多个文字或数字字符，然后是p|
|\W|\w的反置形式，匹配一个或多个非单词字符，如点号句号等|

# 使用场景
## 1、查找指定进程
> ps -ef|grep top

输出
```
zhangti+   8548   8008  0 15:35 ?        00:00:01 nautilus-desktop --force
zhangti+   9501   9450  1 15:39 pts/2    00:00:00 top
zhangti+   9503   9373  0 15:39 pts/1    00:00:00 grep --color=auto top
```
## 2、查找指定进程时不显示grep本身进程
> ps -ef|grep [t]op

输出
```
zhangti+   8548   8008  0 15:35 ?        00:00:01 nautilus-desktop --force
zhangti+   9501   9450  0 15:39 pts/2    00:00:01 top
```
## 3、查找指定进程的个数
> ps -ef|grep -w -c [t]op

输出
```
[zhangtianyu@localhost grep_learning]$ ps -ef|grep -w -c [t]op
1
```
## 4、从文件中读取关键字进行搜索
> ps -ef|grep -w -f pattern.txt

pattern.txt是包含关键字的文件，内容如下：
```
[zhangtianyu@localhost grep_learning]$ cat pattern.txt
[t]op
```
输出
```
[zhangtianyu@localhost grep_learning]$ ps -ef|grep -w -f pattern.txt
zhangti+   9501   9450  0 15:39 pts/2    00:00:03 top
```
## 5、从文件中读取关键词进行搜索且显示行号
> cat target.txt |grep -nf pattern.txt

target.txt是待搜索的文件，内容如下：
```
top
123456top
top123456
adfbdgaga
aaaa
bbbb
cccc
```
输出
```
1:top
2:123456top
3:top123456
```
## 6、从多个文件中查找关键词
> grep 'top' target.txt target_2.txt

target_2.txt是第二个待搜索的文件，内容如下：
```
eeeeeee
ggg
hhh
uuuuuu
top
oweuigtop
top123456
```
输出
```
target.txt:top
target.txt:123456top
target.txt:top123456
target_2.txt:top
target_2.txt:oweuigtop
target_2.txt:top123456
```
## 7、找出以top开头的行
> grep -n '^top' target.txt

输出
```
1:top
3:top123456
```
## 8、找出以top结尾的行
> grep -n 'top$' target.txt

输出
```
1:top
2:123456top
```
## 9、在当前目录中的所有以target开头的文件中查找top
> grep -n 'top' target*

输出
```
target_2.txt:5:top
target_2.txt:6:oweuigtop
target_2.txt:7:top123456
target.txt:1:top
target.txt:2:123456top
target.txt:3:top123456
```
## 10、以递归的方式在文件夹下所有文件中查找export
> grep -r 'top' /home/zhangtianyu/

输出
```
/home/zhangtianyu/Documents/grep_learning/target.txt:top
/home/zhangtianyu/Documents/grep_learning/target.txt:123456top
/home/zhangtianyu/Documents/grep_learning/target.txt:top123456
/home/zhangtianyu/Documents/grep_learning/target_2.txt:top
/home/zhangtianyu/Documents/grep_learning/target_2.txt:oweuigtop
/home/zhangtianyu/Documents/grep_learning/target_2.txt:top123456
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:top --help
/home/zhangtianyu/.bash_history:top -h
/home/zhangtianyu/.bash_history:man top
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:top -d 1
/home/zhangtianyu/.bash_history:top -q
/home/zhangtianyu/.bash_history:top -c
/home/zhangtianyu/.bash_history:top -S
/home/zhangtianyu/.bash_history:top -s
/home/zhangtianyu/.bash_history:top -c
/home/zhangtianyu/.bash_history:top -S
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:top -c
/home/zhangtianyu/.bash_history:top -i
/home/zhangtianyu/.bash_history:top -q
/home/zhangtianyu/.bash_history:top -b
/home/zhangtianyu/.bash_history:top -p 9420
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:man top
/home/zhangtianyu/.bash_history:top
/home/zhangtianyu/.bash_history:top -p 10893
/home/zhangtianyu/.bash_history:top -p 11195
/home/zhangtianyu/.bash_history:top -p 12114
/home/zhangtianyu/.bash_history:top -p 12335
/home/zhangtianyu/.bash_history:top -d 1
/home/zhangtianyu/.bash_history:top
```
## 11、反向查找
> grep -v 'top' target.txt

输出
```
adfbdgaga
aaaa
bbbb
cccc
```
