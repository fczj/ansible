## 服务配置
#熊志标 2017-09-21 增加，检查文件描述符打开数量，5000警告，6000报警
define service{
    use                 lanjing-service
    hostgroup_name      lanjing-file-description
    service_description file description open counts
    check_command       check_fd!5000!6000
    contact_groups      admins
}
```



## 命令command配置
```
#检查文件描述符
define command{
    command_name    check_fd
    command_line    $USER1$/check_nrpe -H $HOSTADDRESS$ -t 1000 -c check_fd -a $ARG1$ $ARG2$
}
```

## 命令检查
```
check_nrpe -t 100 -H 192.168.1.171 -c check_fd -a 5000 6000
```

