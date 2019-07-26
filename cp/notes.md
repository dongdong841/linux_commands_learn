# cp
Linux cp命令主要用于复制文件或目录
# command format
> cp [options] source dest

或
> cp [options] source... directory
## 参数
* -a 此选项通常在复制目录时使用，它保留链接、文件属性，并复制目录下的所有内容。其作用等于dpR参数组合
* -d 复制时保留软链接。这里所说的链接相当于Windows系统中的快捷方式
* -f 覆盖已经存在的目标文件而不给出提示
* -i 与-f选项相反，在覆盖目标文件之前给出提示，要求用户确认是否覆盖，回答"y"时目标文件将被覆盖
* -p 除复制文件的内容外，还把修改时间和访问权限也复制到新文件中
* -r 若给出的源文件是一个目录文件，此时将复制该目录下所有的子目录和文件
* -l 不复制文件，只是生成硬链接文件
* -s 不复制文件，只是生产软链接文件
# examples
## 1、复制文件的场景
■源文件：test_file.cpp    
■源文件的stat：
> [zhangtianyu@localhost test_dir]$ stat test_file.cpp    
  File: ‘test_file.cpp’    
  Size: 95        	Blocks: 8          IO Block: 4096   regular file    
Device: fd00h/64768d	Inode: 75141       Links: 3    
Access: (0664/-rw-rw-r--)  Uid: ( 1000/zhangtianyu)   Gid: ( 1000/zhangtianyu)    
Context: unconfined_u:object_r:user_home_t:s0    
Access: 2019-07-25 16:36:06.568158121 +0800    
Modify: 2019-07-25 13:55:26.683045501 +0800    
Change: 2019-07-26 13:54:21.392023590 +0800    
 Birth: -

### step1、使用无参数的cp指令复制源文件
> cp test_file.cpp test_file.cpp.bak

■test_file.cpp.bak的stat如下：    
> localhost test_dir]$ stat test_file.cpp.bak    
  File: ‘test_file.cpp.bak’    
  Size: 95        	Blocks: 8          IO Block: 4096   regular file    
Device: fd00h/64768d	Inode: 102959033   Links: 1    
Access: (0664/-rw-rw-r--)  Uid: ( 1000/zhangtianyu)   Gid: ( 1000/zhangtianyu)    
Context: unconfined_u:object_r:user_home_t:s0    
Access: 2019-07-26 14:06:43.113058958 +0800    
Modify: 2019-07-26 14:06:43.113058958 +0800    
Change: 2019-07-26 14:06:43.113058958 +0800    
 Birth: -
 
可以看到，普通的cp复制出的文件除了文件内容上没有变化外，Access、Modify、Change、Links、File都发生了改变（由于源文件和复制后的文件都是用户zhangtianyu做的，因此这里的权限没有变化，如果换个用户，就会改变）    
那么有些情况下不希望复制后文件改变权限、Modify，这时可以使用-p参数：
### step2、带-p的文件复制
> cp -p test_file.cpp test_file.cpp.bak    

■test_file.cpp.bak的stat如下：
> [zhangtianyu@localhost test_dir]$ stat test_file.cpp.bak    
  File: ‘test_file.cpp.bak’    
  Size: 95        	Blocks: 8          IO Block: 4096   regular file    
Device: fd00h/64768d	Inode: 102959033   Links: 1    
Access: (0664/-rw-rw-r--)  Uid: ( 1000/zhangtianyu)   Gid: ( 1000/zhangtianyu)    
Context: unconfined_u:object_r:user_home_t:s0    
Access: 2019-07-26 14:06:43.113058958 +0800    
Modify: 2019-07-25 13:55:26.683045501 +0800    
Change: 2019-07-26 14:26:10.332114615 +0800    
 Birth: -    

可以看到，复制后的文件权限和修改时间没有变化
## 2、复制链接的场景
### step1、复制硬链接
