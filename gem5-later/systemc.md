# Gem5 + SystemC

## install systemc

 ~~~bash
 # tip: 在windows下载再上传可能有问题的！！！
 git clone -b 2.3.1a https://github.com/accellera-official/systemc.git
 ~~~

按照`INSTALL`这个文件进行安装systemc

~~~bash
mkdir build
cd build
../configure --prefix=<usr dir>
gmake
gmake install
~~~



## demo-build

在gem5目录下：

~~~bash
# in dir: gem5-stable/
python3 ~/tool/Files/scons312/scons.py scons build/ARM/gem5.opt -j8
python3 ~/tool/Files/scons312/scons.py --with-cxx-config --without-python --without-tcmalloc USE_SYSTEMC=0 build/ARM/libgem5_opt.so -j8

cd util/tlm
scons -j8
~~~

## run demo



### 1 simple demo

创建config.ini代替gem5的配置文件。执行命令：

~~~bash
../../build/ARM/gem5.opt conf/tlm_{master,slave}.py
~~~



虽然会出错，但是在tlm/m5out目录下生成了配置脚本

