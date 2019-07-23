# less
less 与 more 类似，能够分页显示大文件。less不会一次把文件全部读取进来，而是先打开文件读取少量的一部分，之后随着用户的翻动继续读取。因此对于大型文件的打开速度比vim要快。使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动。
# command format
> less [参数] 文件
## 参数说明
* -b <缓冲区大小> 设置缓冲区的大小（__有何用途？单位？__）
* -e 当文件显示结束后，自动退出less
* -f 强迫打开特殊文件，例如外围设备代号、二进制文件等
* -g 只标志最后搜索的关键词
* -i 忽略搜索时的大小写（__不好用？__）
* -m 显示类似more命令的百分比
* -N 显示每行的行号
* -s 显示连续空行为一行
* -o <文件名> 将less 输出的内容在指定文件中保存起来（__如何使用？__）
* -S 行过长时将超出部分舍弃（__行的长度可否设置？__）
* -x <数字> 将"tab"键（文件中的"tab"）显示为规定的数字空格
* -? 显示帮助信息
# commands in less mode
* h 显示帮助信息
* q 退出less
## Moving（screen scroll）
* j downArrow -forward one line
* k upArrow -bakward one line
* rightArrow -left one half screen width
* leftArrow -right one half screen width
* f -forward one window
* b -backward one window
* F -forward forever, like "tail -f"
* r -repaint screen
## searching
* /pattern -从前往后匹配pattern的行
* ?pattern -从后往前匹配pattern的行
* n -向后跳到下一个匹配到的行
* N -向前跳到下一个匹配到的行
## jumping
# examples
1、
