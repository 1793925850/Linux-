# CentOs7命令大全

# 1. 文件与目录操作

## 1.1 ls、cd、cp、pwd

|       命令        |                             说明                             |
| :---------------: | :----------------------------------------------------------: |
|        ls         |                       查看目录中的文件                       |
|       ls -a       |                         显示隐藏文件                         |
|       ls -l       |                         显示详细信息                         |
|      ls -lrt      | 按时间显示文件(l 表示详细列表，r 表示反向排序，t 表示按时间排序) |
|     cd /home      |                       进入“/home”目录                        |
|       cd ..       |                        返回上一级目录                        |
|     cd ../..      |                        返回上两级目录                        |
|       cd -        |                       返回上次所在目录                       |
|  cp file1 file2   |                    将 file1 复制到 file2                     |
|  cp -a dir1 dir2  |                     将 dir1 复制到 dir2                      |
| cp -a /tmp/dir1 . |         复制一个目录到当前工作目录(“.”代表当前目录)          |
|        pwd        |                         显示工作路径                         |

## 1.2 mkdir

|          命令           |       说明       |
| :---------------------: | :--------------: |
|       mkdir dir1        |  创建“dir1”目录  |
|     mkdir dir1 dir2     | 同时创建两个目录 |
| mkdir -p /tmp/dir1/dir2 |  创建一个目录树  |

## 1.3 mv

|     命令     |        说明         |
| :----------: | :-----------------: |
| mv dir1 dir2 | 移动/重命名一个目录 |

## 1.4 rm

|    命令     |             说明             |
| :---------: | :--------------------------: |
| rm -f file1 |       删除“file1”文件        |
| rm -rf dir1 | 删除“dir1”目录及其子目录内容 |

# 2. 查看文件内容

|     命令      |                    说明                     |
| :-----------: | :-----------------------------------------: |
|   cat file1   |  从第一个字节开始正向查看文件”file1“的内容  |
| head -2 file1 |         查看文件”file1“的前两行内容         |
|  more file1   |         查看一个长文件”file1“的内容         |
|   tac file1   | 从最后一行开始反向查看一个文件”file1“的内容 |
| tail -3 file1 |          查看文件”file1“的最后三行          |
|   vim file    |            打开并浏览文件”file“             |

# 3. 文本内容处理

|        命令        |                说明                |
| :----------------: | :--------------------------------: |
|   grep str file1   |      在文件”file1“中查找”str“      |
|  grep ^str file1   | 在文件”file1“中查找以”str“开始的行 |
|  grep [0-9] file1  | 查找”file1“文件中所有包含数字的行  |
| grep str -r dir1/* | 在目录”dir1“及其子目录中查找”str“  |
|  diff file1 file2  |        找出两个文件的不同处        |
| sdiff file1 file2  |   以对比的方式显示两个文件的不同   |



**vi file**：

| 操作 |        说明         |
| :--: | :-----------------: |
|  i   |  进入编辑文本模式   |
| Esc  |  退出编辑文本模式   |
|  :w  |    保存当前修改     |
|  :q  | 不保存并直接退出vim |
| :wq  |    保存并退出vim    |

# 4. 查询操作

|                       命令                        |                      说明                      |
| :-----------------------------------------------: | :--------------------------------------------: |
|                find / -name file1                 |     从“/”开始进入根文件系统查找文件和目录      |
|                find / -user user1                 |        查找属于用户”user1“的文件和目录         |
|           find /home/user1 -name *.bin            |  在目录”/home/user1“中查找以”.bin“结尾的文件   |
|         find /usr/bin -type f -atime +100         |    查找在过去100天内未被使用过的可执行文件     |
|         find /usr/bin -type f -mtime -10          |       查找在10天内被创建或者修改过的文件       |
|                    locate *.ps                    |  寻找以“.ps”结尾的文件，先运行“updatedb”命令   |
|    find -name ‘*.[ch]’ \| xargs grep -E ‘expr’    | 在当前目录及其子目录所有.c和.h文件中查找”expr“ |
| find -type f -print() \| xargs -r0 grep -F ‘expr’ |   在当前目录及其子目录的常规文件中查找”expr“   |
| find -maxdepth 1 -type f \| xargs grep -F ‘expr’  |             在当前目录中查找”expr“             |

# 5. 压缩、解压

|              命令               |                             解析                             |
| :-----------------------------: | :----------------------------------------------------------: |
|           bzip2 file1           |                          压缩 file1                          |
|        bunzip2 file1.bz2        |                        解压 file1.bz2                        |
|           gzip file1            |                          压缩 file1                          |
|          gzip -9 file1          |                      最大程度压缩 file1                      |
|         gunzip file1.gz         |                        解压 file1.gz                         |
|   tar -cvf archive.tar file1    | 把 file1 打包成 archive.tar(-c: 建立压缩档案；-v: 显示所有过程；-f: 使用档案名字，是必须的，是最后一个参数) |
| tar -cvf archive.tar file1 dir1 |              把 file1，dir1 打包成 archive.tar               |
|       tar -tf archive.tar       |                      显示一个包中的内容                      |
|      tar -xvf archive.tar       |                          释放一个包                          |
|  tar -xvf archive.tar -C /tmp   |                  把压缩包释放到 /tmp 目录下                  |
|       zip file1.zip file1       |                  创建一个 zip 格式的压缩包                   |
|   zip -r file1.zip file1 dir1   |           把文件和目录压缩成一个 zip 格式的压缩包            |
|         unzip file1.zip         |             解压一个 zip 格式的压缩包到当前目录              |
|     unzip test.zip -d /tmp/     |            解压一个 zip 格式的压缩包到 /tmp 目录             |

# 6. yum安装器

|              命令              |                         解析                          |
| :----------------------------: | :---------------------------------------------------: |
|    yum -y install [package]    |                 下载并安装一个 rpm 包                 |
| yum localinstall [package.rpm] | 安装一个 rpm 包，使用你自己的软件仓库解决所有依赖关系 |
|         yum -y update          |            更新当前系统中安装的所有 rpm 包            |
|      yum update [package]      |                    更新一个 rpm 包                    |
|      yum remove [package]      |                    删除一个 rpm 包                    |
|            yum list            |              列出当前系统中安装的所有包               |
|      yum search [package]      |                在 rpm 仓库中搜寻软件包                |
|      yum clean [package]       |        清除缓存目录(/var/cache/yum)下的软件包         |
|       yum clean headers        |                    删除所有头文件                     |
|         yum clean all          |               删除所有缓存的包和头文件                |

**什么是RPM**

- RPM 全名 RedHat Package Managerment，是由Red Hat公司提出，被众多Linux发行版本所采用，是一种数据库记录的方式来将所需要的软件安装到到Linux系统的一套软件管理机制
- 它会建立统一的数据库文件，详细记录软件包安装 、卸载等变化信息，能够自动分析软件包依赖关系
- 它最大的特点就是将你要安装的软件先编译过，并且打包成为 RPM 机制的文件，通过打包好的软件里面默认的数据库，记录这个软件要安装的时候必须具备的依赖属性软件。当在你的 Linux 主机安装时，RPM 会先依照软件里面的数据查询Linux 主机的依赖属性软件是否满足，若满足则予以安装，若不满足则不予安装。那么安装的时候就将该软件的信息整个写入 RPM 的数据库中，以便未来的查询、验证与反安装。

**RPM优点**

- 由于已经编译完成井且打包完华，所以软件传输与安装上很方便（不需要再重新编译）
- RPM 在被安装之前，会先检查系统的硬盘容量、操作系统版本等，可避免文件被错误安装。
- RPM 本身提供软件版本信息、依赖属性检查、软件用途说明、软件所含文件等信息；便于了解软件
- RPM 管理使用数据库记录RPM文件的相关参数，便于查询、删除、升级与反安装。

**RPM缺点**

- 由于 RPM 文件是已经打包好的数据，也就是说，里面的数据已经都编译完成了，所以，该软件安装文件几乎只能安装在原本默认的硬件与操作系统版本中。`所以你的主机系统环境必须要与当初建立这个软件安装文件的主机环境相同才行`。

如果我们真的想要安装其他Linux发行版的RPM软件包怎么办？这时候就该用到我们SRMP。



**什么是SRPM**

- SRPM文件里面含有原始码(Source Code)，即SRPM所提供的软件内容并`没有进行编译`，提供的是源代码
- SRPM的文件名是以 ***.src.rpm这种格式来命名
- 虽然SRMP的内容是源代码，但是它仍然含有该软件所需的依赖性软件说明以及所有RPM文件所提供的数据，也提供了参数的配置文件，所以如果我们用的是SRPM的话，安装时，需要先将该软件以RPM管理的方式进行编译，此时SRPM会被编译成RPM文件，然后再将RPM文件安装到Linux系统当中

# 7. 网络相关

|                      命令                       |          解析          |
| :---------------------------------------------: | :--------------------: |
|                  ifconfig eth0                  | 显示一个以太网卡的配置 |
| ifconfig eth0 192.168.1.1 netmask 255.255.255.0 |    配置网卡的IP地址    |
|                   ifdown eth0                   |   禁用“eth0”网络设备   |
|                    ifup eth0                    |   启用“eth0”网络设备   |
|                  iwconfig eth1                  | 显示一个无线网卡的配置 |
|                   iwist scan                    |      显示无线网络      |
|                  ip addr show                   |    显示网卡的IP地址    |

# 8. 系统相关

