备份大佬项目 1.8版本
## docker安装教程

如果你是装过NVjdc 先看看后面1.2以前如何更新之1.2升级说明

1拉源码
国内
```
git clone https://ghproxy.com/https://github.com/liunian6/Nolan1.9.git /root/nolanjdc
```

2 拉取基础镜像以后不需要拉取镜像了
```
sudo docker pull nolanhzy/nvjdc:latest
```

3 执行命令

```
yum install wget unzip -y
```

4创建一个目录放配置

```
 cd /root/nolanjdc
```
```
mkdir -p  Config && cd Config
```

5下载config.json 配置文件 并且修改自己的配置 不能缺少
源码库已经关闭了Json 需要自行需找。

```
wget -O Config.json  https://github.com/liunian6/Scripts/blob/unke/Config.json
```
国内请使用
 ```
wget -O Config.json   https://ghproxy.com/https://github.com/liunian6/Scripts/blob/unke/Config.json
```

6 回到nolanjdc目录创建chromium文件夹并进入

```
cd /root/nolanjdc && mkdir -p  .local-chromium/Linux-884014 && cd .local-chromium/Linux-884014
```

7下载 chromium 

```
wget https://mirrors.huaweicloud.com/chromium-browser-snapshots/Linux_x64/884014/chrome-linux.zip && unzip chrome-linux.zip
```

8删除刚刚下载的压缩包 

```
rm  -f chrome-linux.zip
```

9回到刚刚创建的目录

```
cd  /root/nolanjdc
```



10启动镜像

```
sudo docker run   --name nolanjdc -p 5703:80 -d  -v  "$(pwd)":/app \
-v /etc/localtime:/etc/localtime:ro \
-it --privileged=true  nolanhzy/nvjdc:latest
```
上面是一条命令不是多条

11查看 日志 

```
docker logs -f nolanjdc 
```

  

出现 NETJDC  started 即可 



删除容器
```
docker rm -f nolanjdc 
```
然后从步骤9开始即可

后续更新只需要按照下方代码更新即可


## 更新

```
cd /root/nolanjdc
```
```
docker stop nolanjdc
```
```
git pull
```
```
docker start nolanjdc
```


脚本自用，别偷
