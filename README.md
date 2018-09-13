# tars-docker build in centos  
在docker 自行安装Tars  

## tars 安装  

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
安装之后tars 目录在：/usr/local/app/tars/  
web的目录在：/usr/local/resin/  

执行一下脚本启动tars主控等服务、以及web管理台：

* tars_start.sh
ps -ef|grep tars
```shell
root       865     1  0 10:22 pts/0    00:00:00 /usr/local/app/tars/tarsregistry/bin/tarsregistry --config=/usr/local/app/tars/tarsregistry/conf/tarsregistry.conf
root       874     1  0 10:22 pts/0    00:00:00 /usr/local/app/tars/tarsAdminRegistry/bin/tarsAdminRegistry --config=/usr/local/app/tars/tarsAdminRegistry/conf/adminregistry.conf
root       894     1  0 10:22 pts/0    00:00:00 /usr/local/app/tars/tarsconfig/bin/tarsconfig --config=/usr/local/app/tars/tarsconfig/conf/tarsconfig.conf
root       903     1  0 10:22 pts/0    00:00:00 /usr/local/app/tars/tarspatch/bin/tarspatch --config=/usr/local/app/tars/tarspatch/conf/tarspatch.conf
root       939     1  0 10:22 ?        00:00:00 rsync --address=172.17.0.2 --daemon --config=/usr/local/app/tars/tarspatch/conf/rsync.conf
root       941     1  0 10:22 ?        00:00:00 /usr/local/app/tars/tarsnode/bin/tarsnode --locator=tars.tarsregistry.QueryObj@tcp -h  172.17.0.2 -p 17890 --config=/usr/local/app/tars/tarsnode/conf/tarsnode.conf
```
在访问：localhost:9090 

## 配置
* 如果管理台链接哪个主控是在这个配置中进行配置的：
/usr/local/resin/webapps/tars/WEB-INF/classes/tars.conf

* 发布包上传相关的配置：
/usr/local/app/tars/tarspatch/conf/rsync.conf

