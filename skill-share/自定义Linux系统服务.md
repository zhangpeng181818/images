一、编写服务脚本

以nursed服务为例:

进入 /usr/lib/systemd/system, 新建nursed.service文件,写入如下内容。

```shell
[Unit]
#服务描述
Description=Mdkmed Nursed Service
#设置在某个服务启动后启动：这里为指mysql服务启动后再启动本服务
After=network.target mysqld.service

[Service]
#后台运行的形式
Type=forking
#启动命令，执行该脚本
ExecStart=/usr/nursed/start-nursed.sh
#重启命令，执行该脚本
ExecReload=/usr/nursed/restart-nursed.sh
#停止命令，执行该脚本
ExecStop=/usr/nursed/stop-nursed.sh
#启动失败时，执行重启命令
Restart=on-failure
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

启动脚本：start-nursed.sh

```shell
#!/usr/bin/env bash

nohup java -jar /usr/nursed/nursed-1.0.0-SNAPSHOT.jar >/dev/null 2>/var/log/nursed/errors.log &
```

停止服务脚本：stop-nursed.sh

```shell
#!/usr/bin/env sh

kill -9 $(ps aux | grep nursed-1.0 | awk 'NR==1{print $2}')
```

重启服务脚本：restart-nursed.sh

```shell
#!/usr/bin/env sh

./stop-nursed.sh
./start-nursed.sh
```

![5](https://raw.githubusercontent.com/wiki/zhangpeng181818/images/skill-share/5.png)

二、加载服务并设置启动

```shell
systemctl reload *.service #重新加载服务配置文件

然后就可以启动服务了,

systemctl start nursed.service即可

设置开机启动: systemctl enable nuresd.service
```

三、常用命令介绍

```shell
systemctl常见命令:

systemctl is-enabled servicename.service #查询服务是否开机启动
systemctl enable *.service #开机运行服务
systemctl disable *.service #取消开机运行
systemctl start *.service #启动服务
systemctl stop *.service #停止服务
systemctl restart *.service #重启服务
systemctl reload *.service #重新加载服务配置文件
systemctl status *.service #查询服务运行状态
systemctl --failed #显示启动失败的服务
```

