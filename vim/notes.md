# vim
linux下的一款非常强大的文件编辑器
# command format
> vim [arguments] [file ..]
## 参数
* -v vi模式（类似vi）
* -e ex模式（类似ex）
* -E 改进的ex模式
* -d diff模式（类似vimdiff）
* -R 只读模式
* -b 二进制模式
* -n 没有swap模式
* -o 打开多个文件，为每个文件创建一个窗口
* -p 打开多个文件，为每个文件创建一个标签页
* \+ 打开文件后光标停在最后一行
* +\<NUM\> 打开文件后光标停在第NUM行
* -h 显示帮助信息
* --version 显示vim版本信息（实例说明参见details目录下的version_para.md）
# normal mode
## 常用翻页移动命令
* h、j、k、l 左、下、上、右（尽量不要用方向键，因为手会离开键盘，影响输入速度）
* gg,G 光标移动到文件第一行、最后一行
* n% 光标移动到文件任意百分比位置
* ngg 光标移动到文件的第N行
* ctrl+f,Ctrl+b 向后翻页，向前翻页
* H,M,L 光标定位到当前屏幕最上方、中间、最下面
* zt,zz,zb 当前行移动到屏幕的最上方、中间、最下面
* nj,nk 从当前行光标向下、上移动N行
* w, b (W、B) 向前、后移动一个word (注意 word 和 WORD 区别)
* ^,0 光标移动到行首
* $ 光标移动到行尾
* ctrl+e,ctrl+y 光标文字同时向上、下移动一行
## 历史文件跳转
### jumplist
* :jump 列出所有的访问点
* ctrl+i 跳转到下一个访问点
* n ctrl+i 向后跳转到第n个访问点
* n ctrl+o 向前跳转到第n个访问点
### changelist
* g; 向后移动一个修改点
* g, 向前移动一个修改点
* :changes 列出所有的修改点
### marks
* :marks 列出所有的标记点
* m{mark} \'{mark}\'可以是a~z或A~Z中任意字符，使用此字符对当前光标位置做标记
* \`{mark},\'{mark} 光标跳转到{mark}标记处
## 一定范围内执行命令
* :%d %表示文档全部，即删除全部内容
* :n,m d 删除n行到m行
* :.,.+100d 从当前行到当前行+100执行d命令
* :.,'a d 从当前行到mark 'a，执行d命令
* :.,\/regex\/d 从当前行到匹配行，执行d命令
