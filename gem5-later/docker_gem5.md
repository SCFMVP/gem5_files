>[使用docker安装gem5](https://blog.csdn.net/m0_37340681/article/details/122168674)
# 一、在线安装
## 安装docker(ubuntu)

~~~bash
# 安装docker
mkdir ~/docker
cd ~/docker
curl -sSL https://get.docker.com/ | sh
~~~




~~~bash
# 查看docker版本
sudo docker version
~~~



~~~bash
# 更换镜像源
sudo su -
cat >> /etc/docker/daemon.json <<- EOF
{
  "registry-mirrors": ["https://registry.docker-cn.com"]
}
EOF
systemctl restart docker
exit
~~~



## 下载Docker镜像

~~~bash
docker pull lijiali1101/gem5
# 官方给的下载不下来
# docker pull  gcr.io/gem5-test/ubuntu-20.04_all-dependencies:v21-2
~~~

## 下载gem5

~~~bash
git clone https://github.com/gem5/gem5.git
~~~

进入docker镜像：

```bash
docker run --volume /home/ubuntu/gem5:/gem5 --rm -it lijiali1101/gem5
```

## 测试

~~~bash
cd gem5
~~~

和gem5操作完全一样了

# 二、离线安装

## 安装docker

> https://docs.docker.com/engine/install/binaries/

下载[docker](https://download.docker.com/linux/static/stable/x86_64/)文件，解压`docker-17.03.2-ce.tgz`.



无法安装到指定位置:broken_heart:进行不下去了:no_entry:



把带路径的参数都指定一下，好像能装上哎。



不过还是不能用！

## 下载docker镜像

1、官方下载：

[Building gem5](https://www.gem5.org/documentation/general_docs/building)

* Ubuntu 20.04 with all optional dependencies: [gcr.io/gem5-test/ubuntu-20.04_all-dependencies:v21-2](https://gcr.io/gem5-test/ubuntu-20.04_all-dependencies:v21-2) ([source Dockerfile](https://gem5.googlesource.com/public/gem5/+/refs/heads/stable/util/dockerfiles/ubuntu-20.04_all-dependencies/Dockerfile)).

* Ubuntu 20.04 with minimum dependencies: [gcr.io/gem5-test/ubuntu-20.04_all-dependencies:v21-2](https://gcr.io/gem5-test/ubuntu-20.04_min-dependencies:v21-2) ([source Dockerfile](https://gem5.googlesource.com/public/gem5/+/refs/heads/stable/util/dockerfiles/ubuntu-20.04_min-dependencies/Dockerfile)).

* Ubuntu 18.04 with all optional dependencies: [gcr.io/gem5-test/ubuntu-18.04_all-dependencies:v21-2](https://gcr.io/gem5-test/ubuntu-18.04_all-dependencies:v21-2) ([source Dockerfile](https://gem5.googlesource.com/public/gem5/+/refs/heads/stable/util/dockerfiles/ubuntu-18.04_all-dependencies/Dockerfile)).

2、官方如果实在没办法下载的话：

在这个网页下载：[lijiali1101/gem5](lijiali1101/gem5)

~~~bash
docker pull lijiali1101/gem5  # 网友的镜像
# https://www.jianshu.com/p/729d755ace65
docker save <image_id> -o <path/gem5.tar> # 保持镜像
dorker load -i <path/gem5.tar> # 离线导入镜像
~~~

3、或者按2的办法把Windows docker desktop的镜像导出使用

## 下载gem5

~~~bash
git clone https://github.com/gem5/gem5.git
~~~



进入docker镜像：

```bash
docker run --volume /home/ubuntu/gem5:/gem5 --rm -it lijiali1101/gem5
```



## 测试

# 三、windows docker

## 安装

有白名单阻碍，无法安装。。。。

## 其他步骤同一

# 四、101服务器内虚拟机

## 安装docker

通过P盘把docker的文件拷贝到虚拟机里面的vmware（再用共享文件夹）。

~~~bash
# 解压
tar zxvf docker-17.03.2-ce.tgz
# cp
cp docker/* /usr/bin/
# start 
dockerd &
# verify, need pull
docker run hello-world
~~~

## pull images

~~~bash
docker pull lijiali1101/gem5
~~~



