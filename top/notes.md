# top
常用来监控Linux的系统状况，比如cpu、内存的使用，监控的内容会定时刷新
# command format
> top -hv | -bcHiOSs -d secs -n max -u|U user -p pid(s) -o field -w [cols]
## 参数
* -d NUM 改变显示的更新速度,NUM为秒
* -i 不显示任何闲置 (idle) 或无用 (zombie) 的进程
* -n NUN 更新的次数，完成后将会退出 top
* -b 以批处理的形式显示top内容
* p pid 进程列表中仅列出Pid进程
# top显示内容说明
