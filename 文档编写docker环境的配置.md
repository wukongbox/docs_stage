

##安装docker 
* 下载镜像 

```
docker pull registry.cn-hangzhou.aliyuncs.com/weeknd/weeknd:wukongbox_docs
```

* 查看镜像ID（imageID） 

```
docker images
```


* 启动容器 
```
   docker run -p 8001:8001 -p 8888:8888 --name mkdocs -itd {ImageID} /bin/bash
```
 * 本地创建目录（我这里创建是/root/api，/root/admin-book，/root/manual三个目录） 
   关系拓扑 
   本地/root/api ------->容器/home/documents/docs/api

* 停止mkdocs （如果在运行）
```
docker stop mkdocs
```

* 启动容器
``` 
docker run -p 8001:8001 -p 8888:8888 \ 
--name 新的容器名称 \ 
-v /root/api/:/home/documents/docs/api/ \ 
-v /root/admin-book/:/home/documents/docs/admin-book/ \ 
-v /root/manual/:/home/documents/docs/manual/ \ 
-d 镜像ID
```

Note：如果遇到文件映射不到容器内的情况，可以关闭selinux



* 启动浏览器查看服务（jupyter登陆密码为123456）

```

    <a href="http://localhost:8001/"><span class="s3">http://localhost:8001</span></a> 
    <a href="http://localhost:8888/"><span class="s3">http://localhost:8888</span></a>
    Note：如果使用的虚拟机，请将localhost修改为虚拟机的ip，iptables规则开放这两个端口，或者关闭虚拟机的防火墙。


```

* 再次启动容器

```
docker start mkdocs
```





##删除docker镜像的命令

删除docker imager 
docker ps -a 
docker stop names 
docker rm CONTAINER ID 
docker images 
docker rmi imageid