```shell
功能：获取host文件中，ip、用户名、密码、端口，为后面功能做准备。		
#! /usr/bin/bash

file=host.txt

for ip in $(awk '/^[^#-]/{print $1}' $file);do
        #echo $ip
        user=$(awk -v I=$ip 'I==$1{print $2}' $file)
        pass=$(awk -v I=$ip 'I==$1{print $3}' $file)
        port=$(awk -v I=$ip 'I==$1{print $4}' $file)
        echo "$ip $user $pass $port"
done

注意点：
在这个脚本中,`awk` 命令被用来从 `host.txt` 文件中提取所需的信息。以下是对 `awk` 用法的解释:

1. `awk '/^[^#-]/{print $1}' $file`
   - `awk` 命令用于处理 `$file` 文件(即 `host.txt`)。
   - `/^[^#-]/` 是一个正则表达式,匹配不以 `#` 或 `-` 开头的行。
   - `{print $1}` 表示打印出匹配行的第一个字段,也就是 IP 地址。

2. `awk -v I=$ip 'I==$1{print $2}' $file`
   - `awk -v I=$ip` 将 `$ip` 的值赋给变量 `I`。
   - `I==$1{print $2}` 表示:如果第一个字段(`$1`)等于变量 `I` 的值(即当前的 IP 地址),则打印出第二个字段,也就是用户名。

3. `awk -v I=$ip 'I==$1{print $3}' $file`
   - 同上,但这次打印出第三个字段,即密码。

4. `awk -v I=$ip 'I==$1{print $4}' $file`
   - 同上,但这次打印出第四个字段,即端口号。

总的来说,`awk` 命令通过对文件内容进行模式匹配和字段提取,帮助这个脚本从 `host.txt` 文件中获取所需的连接信息。
```

```shell
#主机                   帐号            密码            端口
------------------------------------------
192.168.1.1             root            123456          22
192.168.1.2             root            123456          22
192.168.1.3             root            123456          22
192.168.1.4             root            123456          22
```