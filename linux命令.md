
<!-- TOC -->

- [linux 命令](#linux-命令)
- [vim 命令](#vim-命令)

<!-- /TOC -->
## linux 命令
| 命令      |     作用 |
| :-------- | :--------|
| ls    |   列出目录 |
|ls -al |   使用格式化列出隐藏文件|
| cd dir  |   进入目录dir |
|cd  |  进入home目录|
|pwd  |  显示当前目录|
| mkdir dir| 创建目录dir |
| rm file | 删除文件 file |
| rm -r dir | 删除文件 dir |
| rm -f file | 强制删除file |
| rm -rf dir | 强制删除dir |
| cp file1 file2 | 将file1 复制到 file2 |
| cp -r dir1 dir2| 讲dir1复制到dir2;如果dir2不存在就创建它 |
| mv file1 file2 | 将file1重命名或到file2;如果flie是存在的目录就是把file1 移动file2 中 |
| in -s file link | 创建 file 的符号连接 link |
| touch file | 创建file文件 |
| cat > file | 将标准输入添加到file |
| more file | 查看file的内容 |
| tail -f file | 从后10行开始查看file的内容 |
| man command | 显示command的说明手册 |
| ps | 显示当前的活动进程 |
| top | 显示当前的活动进程 |
| kill pid | 杀掉进程 id pid |
| killall proc | 杀掉所有名为 proc 的进程 |
| chmod octal file | 更改file的权限 |
| grep pattern files | 搜索 files 中匹配pattern的内容 |
| df | 显示磁盘占用情况 |
| du | 显示目录空间占用情况 |
| tar xzf file.tar.gz | 使用Gzip解压tar文件 |
| tar xjf file.tar.bz2 | 使用Bzip2解压tar文件 |
| ping host | ping host 并输出结果 |
| wget file | 下载file | 

## vim 命令
| 命令      |     作用 |
| :-------- | :--------|
| vi abc.txt | 打开 abc.txt |
| i or a | 使abc.txt可编辑 |
| ESC | 退出编辑模式 |
| :wq | 保存并退出 |
| :q! | 不保存退出 |

