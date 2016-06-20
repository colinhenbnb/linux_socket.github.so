### mac iterm 环境配置
windows下一直使用xshell,特别喜欢xshell支持的快捷键输入密码，当然mac下有破解版的secureCRT，但是蛋疼的界面看起来太杂乱了，还是iterm使用起来精简清晰；习惯了使用xshell，当然需要把iterm配置成xshell工作模式啦
#### 1、官网下载iterm2,并安装；
#### 2、配置快捷键

将快捷键配置为存储的机器名或者对应机器名的几个常用密码，（机器名：shift+F1..n,密码F1..n）使用起来特别方便；

	command+O打开profile编辑界面；	
	创建新的profile或者修改default profile；
	选择key选项；里面配置对应的快捷键（切记action 选择send text,\n 标示换行）对应的操作即可
	
好啦，关闭之后在iterm键入快捷键，即可输入对应的text;

#### 3、session clone
iterm其实并不支持session clone;command+t只能是复制窗口，在办公时候登入relay需要重复输入token密码（一个密码只能输入一次，一般人我不告诉他），也是醉醉的；

但是，可以用另外的方法替换session clone 的模式；参考：http://www.cnblogs.com/rollenholt/p/4531199.html

     在~/.ssh里面创建一个config文件
     输入： host *
           ControlMaster auto
           ControlPath ~/.ssh/master-%r@%h:%p
           
这样command + t 即可复制session了










### unix socket 编程
#### 1、socket(int domain, int type, int protocol)

domain：协议域，又称协议族（family）。常用的协议族有AF_INET、AF_INET6、AF_LOCAL（或称AF_UNIX，Unix域Socket）、AF_ROUTE等。协议族决定了socket的地址类型，在通信中必须采用对应的地址，如AF_INET决定了要用ipv4地址（32位的）与端口号（16位的）的组合、AF_UNIX决定了要用一个绝对路径名作为地址。

type：指定Socket类型。常用的socket类型有SOCK_STREAM、SOCK_DGRAM、SOCK_RAW、SOCK_PACKET、SOCK_SEQPACKET等。流式Socket（SOCK_STREAM）是一种面向连接的Socket，针对于面向连接的TCP服务应用。数据报式Socket（SOCK_DGRAM）是一种无连接的Socket，对应于无连接的UDP服务应用。

protocol：指定协议。常用协议有IPPROTO_TCP、IPPROTO_UDP、IPPROTO_STCP、IPPROTO_TIPC等，分别对应TCP传输协议、UDP传输协议、STCP传输协议、TIPC传输协议。

注意：1.type和protocol不可以随意组合，如SOCK_STREAM不可以跟IPPROTO_UDP组合。当第三个参数为0时，会自动选择第二个参数类型对应的默认协议。



#### 2、ioctl函数获取本地所有ip
ioctl (fd, SIOCGIFCONF, (char *) &ifc) 

关键参数SIOCGIFCONF




#### svn 

创建分支：
svn copy url new_url -m "xxxx"

添加文件：
svn add file

添加目录：
svn import -m "import directory" url


与控制中心版本一致
svn up;




#### 代码规范
strdup 用 strndup替换 strcat 用strncat替换





##unix 追问题

strace -p pid




# 深入理解nginx

uri:统一描资源述符
url:统一资源定位符