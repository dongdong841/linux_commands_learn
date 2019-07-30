# top
常用来监控Linux的系统状况，比如cpu、内存的使用，监控的内容会定时刷新
# command format
> top -hv | -bcHiOSs -d secs -n max -u|U user -p pid(s) -o field -w [cols]
## 参数
* -d NUM 改变显示的更新速度,NUM为秒
* -i 不显示任何闲置 (idle) 或无用 (zombie) 的进程
* -n NUN 更新的次数，完成后将会退出 top
* -p Pid 进程列表中仅列出Pid进程
# top显示内容说明
![top_normal.PNG](https://github.com/dongdong841/linux_commands_learn/blob/master/top/top_normal.PNG)
## 第一行
* top 当前时间
* up 系统从启东开始到当前的时间
* users 登入的用户数
* load average 1分钟、5分钟、15分钟的负载情况
* -b 以批处理的形式显示top内容
* p pid 进程列表中仅
## 第二行
* total 总进程数
* running 运行中的进程数
* sleeping 休眠中的进程数
* stop stop状态的进程数
* zombie 僵尸进程数
## 第三行 cpu状态
* us — 用户空间占用CPU的百分比
* sy — 内核空间占用CPU的百分比
* ni — 改变过优先级的进程占用CPU的百分比
* id — 空闲CPU百分比
* wa — IO等待占用CPU的百分比
* hi — 硬中断（Hardware IRQ）占用CPU的百分比
* si — 软中断（Software Interrupts）占用CPU的百分比
## 第四行 内存状态
* total 总内存
* free 空闲内存
* used 使用了的内存
* buff/cache 缓存的内存
## 第五行 swap状态
* total — 交换区总量
* used — 使用的交换区总量
* free — 空闲交换区总量
* cached — 缓冲的交换区总量
