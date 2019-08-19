# stat
Linux stat命令用于显示inode内容。
# command format
> stat [文件或目录]
# example
## 1、打印文件的inode内容
```
[zhangtianyu@localhost dir_test]$ stat file_test.txt 
  文件："file_test.txt"
  大小：0         	块：0          IO 块：4096   普通空文件
设备：fd00h/64768d	Inode：222898      硬链接：1
权限：(0664/-rw-rw-r--)  Uid：( 1000/zhangtianyu)   Gid：( 1000/zhangtianyu)
环境：unconfined_u:object_r:user_home_t:s0
最近访问：2019-08-19 09:38:58.720556652 +0800
最近更改：2019-08-19 09:38:38.575555439 +0800
最近改动：2019-08-19 09:42:07.724568024 +0800
创建时间：-
```
■文件：文件名称    
■大小：文件大小，由于是空文件，所以大小为0    
■块：文件所占用的块数量，由于是空文件，所以大小为0    
■IO块：文件输出输入设备所使用的块数量    
■设备：设备号    
■Inode：inode号    
■硬链接：硬链接数量    
■权限：文档权限    
■Uid：    
■Gid:    
■环境：    
■最近访问：最近的访问时间    
■最近更改：文件内容发生变化的时间    
■最近改动：文件改动时间（文件复制、移动、保存、文件数据修改、访问，属性修改）    
■创建时间：？？？    
