# tars-docker build in centos
在docker 自行安装Tars

## 安装步骤  
启动docker 实例
```shell
docker run -itv /Users/nano/project/Tars/:/workerspace/Tars -p 9090:8080 -p 9091:873 --cap-add sys_ptrace leeqx/centos-tars:latest /bin/bash
```
执行完install_env.sh 之后，可以看到当前目录下生成几个shell脚本
```shell
-rwxr-xr-x  1 root root   45 Sep  6 10:32 mysql_start.sh
-rwxr-xr-x  1 root root  142 Sep 11 20:10 resin_start.sh
-rwxr-xr-x  1 root root   84 Sep 11 20:11 resin_stop.sh
-rw-r--r--  1 root root  194 Sep 11 10:41 tars_start.sh
```
[root@3881d3f3baa1 tars]# vi /usr/local/resin/webapps/tars/WEB-INF/classes/tars.conf
