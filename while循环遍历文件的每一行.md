```shell
功能循环读取文件中的每一行数据
#! /usr/bin/bash

file="host.txt"
#IFS=[.]
while read -r line;do
        echo $line
        done < $file
        
注意：IFS="[,]" 设置了输入字段分隔符(IFS)为方括号和逗号。这意味着 read 命令会将输入行按照这些分隔符进行拆分，不指定IFS默认是换行符号
```

