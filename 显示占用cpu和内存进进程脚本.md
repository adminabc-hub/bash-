```shell
功能：显示占用cpu和内存前10的进程，运行脚本时可以加一个参数，显示多少个进程
#!/usr/bin/bash
if [ -z $1 ];then
    echo "cpu================================================="
    ps -eo user,pid,%cpu,%mem,args --sort=-%cpu | head -n 10
    echo "mem================================================="
    ps -eo user,pid,%cpu,%mem,args --sort=-%mem | head -n 10
else
   echo "cpu================================================="
   ps -eo user,pid,%cpu,%mem,args --sort=-%cpu | head -n $(expr $1 + 1)
   echo "mem================================================="
   ps -eo user,pid,%cpu,%mem,args --sort=-%mem | head -n $(expr $1 + 1)
fi

```

