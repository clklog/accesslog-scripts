# 安装vector

 日志服务器上安装vector. 下载地址  https://vector.dev/download/

## windows 

假设vector 安装地址 D:\Vector\

命令行启动

```
D:\Vector\bin\vector  --config D:\Vector\config\vector_iis.yaml
```

创建服务

``` 
sc.exe create vector binpath="D:\Vector\bin\vector  --config D:\Vector\config\vector_iis.yaml"
``` 

## linux

默认服务位置

```
/usr/lib/systemd/system/vector.service
```

默认配置文件

```
/etc/vector/vector.yaml
```

启动停止命令

```
systemctl restart/stop vector

```

# 采集iis

## 修改配置

假设 iis日志在目录 D:\WWW_LOG\W3SVC1

创建目录 D:\Vector\iis_data

根据实际情况修改 vector_iis.yaml 中以下内容

- vector数据目录 : D:\\Vector\\iis_data
- iis日志目录 : D:\\WWW_LOG\\W3SVC1\\*.log
- kafka 地址 : 192.168.1.164:9092
- kafka topic : accesslog
- 解析失败的日志存储文件名 : D:\\Vector\\iis_data\\iis_droped.txt
- 根据iis日志格式修改parse_grok中的grok表达式

# 采集nginx access

## 修改配置

假设access日志文件地址 /var/log/nginx/access.log

创建vector数据目录 /etc/vector/access_data

根据实际情况修改 vector_access.yaml 中以下内容

- vector数据目录 : /etc/vector/access_data
- nginx access日志文件地址 : /var/log/nginx/access.log
- kafka 地址 : 192.168.1.164:9092
- kafka topic : accesslog
- 解析失败的日志存储文件名 : /etc/vector/access_data/access_droped.txt
- 根据access日志格式修改parse_grok中的grok表达式
