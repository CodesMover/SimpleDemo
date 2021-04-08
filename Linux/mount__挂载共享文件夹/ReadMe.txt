cifs的意思是通用网络文件系统， mount.cifs用于挂载linux的CIFS文件系统，当用-t cifs命令的时候间接的涉及了mount(8)命令。
这个命令只能在linux上执行，以及内核必须支持cifs文件系统。cifs协议的前身是smb协议，被大部分的windows、商业服务器、存储应用支持。
（mount.cifs跟mount -t cifs唯一的区别就是mount.cifs在samba软件包里，而mount在util-linux软件包里。)

mount_C++.sh
username		//Windows端用户名
password		//Windows端用户密码
//Linux  uid，gid查看
id +用户名

//192.168.100.232/C		//Windows的ip地址及共享目录
/home/hai/Projects/C++	//Linux的目录