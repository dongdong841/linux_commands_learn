# less
less 与 more 类似，但使用 less 可以随意浏览文件，而 more 仅能向前移动，却不能向后移动，而且 less 在查看之前不会加载整个文件。
# command format
> less [参数] 文件
## 参数说明
* -b <缓冲区大小> 设置缓冲区的大小（有何用途？单位？）
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

# examples
1、
