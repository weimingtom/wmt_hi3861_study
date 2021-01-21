# wmt_hi3861_study
My Hi3861 study

## template project  
* search baidupan, code-1.0.tar.gz  
* build comomand: $ python3 build.py wifiiot  

## my own risc-v gcc toolchain build  
* search baidupan, gcc_riscv32_v1_not_tested.tar.gz  
* test pass  

## (TODO) risc-v gcc toolchain build method    
* search baidupan, riscv-gcc-riscv-gcc-7.3.0.zip  

## Ref  
* Hi3861开发板介绍, 快速开始, in HarmonyOS Device    
https://device.harmonyos.com/cn/docs/start/introduce/oem_wifi_start_des-0000001050168548  
https://gitee.com/openharmony/docs/blob/master/quick-start/Readme-CN.md  

* hihope  
http://www.hihope.org/hihope/index  

* HiHope开发者社区, in 电子发烧友论坛    
https://bbs.elecfans.com/group_1429  

* gn、ninja的安装-Ubuntu18.04  
https://blog.csdn.net/qiuguolu1108/article/details/103842556  

* 开发Hi3861第一个示例程序  
https://device.harmonyos.com/cn/docs/start/introduce/oem_wifi_start_helloword-0000001051930719  

* 使用HiBurn烧录鸿蒙.bin文件到Hi3861开发板  
https://harmonyos.51cto.com/posts/1197  

* HUAWEI DevEco Device Tool 1.0 Beta1  
https://device.harmonyos.com/cn/ide#download  
Unzip vscode plugin file and get HiBurn exe for hi3861     

* 使用HiBurn烧录鸿蒙.bin文件到Hi3861开发板  
https://www.cnblogs.com/developer-huawei/p/14025909.html  

## hiburn烧录, from my weibo    
关于hi3861的烧录问题，我试了一下，方法是设置一下hiburn，然后点击连接，  
等待烧录，然后按开发板上的reset按钮，  
就会自动执行烧录（出现3次烧录进度条），然后就成功了，拔掉USB线重新连接PC  
就能看到串口输出（默认似乎不执行东西，  如果要添加代码，需要看官方文档自己写）  
（1）获取hiburn：我比较奇怪这个程序好像会被误报病毒。。。关于这个程序的获取，  
可以参考这篇：https://harmonyos.51cto.com/posts/1197   
（2）设置hiburn：COM口刷新后选择，选择allinone固件，勾选Auto burn，点击Connect，  
然后按板载的reset按钮，然后等待烧录的3次进度条结束  

## 快速使用hpm-cli编译鸿蒙组件   
https://harmonyos.51cto.com/posts/805  
$ npm install -g @ohos/hpm-cli  

## hpm包管理器   
https://hpm.harmonyos.com/#/cn/bundles  

## how to compile risc-v toolchain for hi3861, by my weibo  
说说我上星期在xubuntu 20.04 64位上编译risc-v工具链的体会。很困难，有很多坑，  
hi3861的官网虽然给了参数，但如果照他所说的来做可能会失败。hi3861的编译方法是  
一个简化版，官方给的完整的risc-v工具链编译是很复杂的（可能会很简单），但hi3861  
是逐个库来编译，依次是tools（除了gcc、g++以外的命令，包括一些汇编工具）、newlib  
（相当于c库），以及最后的gcc（剩下的gcc和g++命令），不过这里有个非常棘手的问题，  
就是怎么解决newlib和gcc之间相互依赖的关系，我的做法是先编译一个不需要newlib头  
文件的gcc，方法是在官方给的参数基础上，把gcc的编译参数修改成这样：  
--disable-libssp --enable-languages=c --without-headers，  
取代原本的--enable-libssp --enable-languages=c,c++和  
--with-headers。这样可以暂时避免对newlib的依赖，然后再想  
办法重新编译一次gcc  

## 鸿蒙OS开发者社区, 电子发烧友论坛  
https://bbs.elecfans.com/harmonyos  

## LiteOS Studio, support hi3861  
https://liteos.gitee.io/liteos_studio/#/project_wifiiot  
https://gitee.com/LiteOS/LiteOS_Studio  
https://gitee.com/openharmony/applications_sample_wifi_iot  
https://gitee.com/hihopeorg/applications_sample_wifi_iot  

## hcc_riscv32_win缺失问题  
关于昨天hi3861和LiteOS Studio的问题，有几个可能的原因：  
（1）gitee官网文档所说的LiteOS Studio版本似乎是比较低的，  
跟hihope官方给的LiteOS Studio版本不同，貌似后者的版本更高（安装时显示为试用版）  
https://liteos.gitee.io/liteos_studio  
http://www.hihope.org/download/AllDocuments  
（2）网上也有人出现hcc_riscv32_win工具链不存在，可能也是上面的原因导致  
https://bbs.elecfans.com/jishu_1998668_1_1.html  
C:\用户\Administrator\.huawei-liteos-studio\tools\hi3861  
（3）究竟LiteOS Studio和HUAWEI DevEco Device Tool哪个才是正统，  
我觉得可能华为自己也说不清，大概后者只是把前者改个名字，但后者可能  
会有别的用途或者打算，或者只是单纯想和鸿蒙扯上关系罢了（很可能背后  
也是一个团队搞的）  
(4) 我发现如果装过最新版的LiteOS Studio，再装HiHope的试用版LiteOS Studio  
（在Hi3861 SDK压缩包中得到exe安装包），还是会出问题，因为两者的插件版本  
号出现冲突，前者的版本旧，但插件的版本新，后者则反过来。导致插件无法升级  
。。。看官方什么时候把试用版合并到最新版，就不会有这个吐血的问题了。  
如果只是想得到hcc_riscv32_win这个工具链，可以直接在试用版安装目录下找到  
vsix插件，用7zip解压就能看到，因为这个插件超过50MB，其实一眼就能看出里面  
是夹带了一个很大的文件，如果你只是在gitee下载hi3861的vsix插件，连10MB都  
不到。。。  
(5) 其实还有一个解决办法，就是手动删除c盘Users目录下面用户名目录下的  
.huawei-liteos-studio文件夹，官方不会去考虑有人既装正式版又装试用版的  
LiteOS Studio的情况，只能自己手工去复位到从来没安装过的状态  6）

## 我大致成功在windows下编译了hi3861的SDK例子工程了  
（1）python3改成python，调用windows安装的python  
（2）dd和sha256sum命令，用busybox解决  
（3）hcc_riscv32_win工具链，要在hihope提供的LiteOS Studio里面找  
