# wmt_hi3861_study
My Hi3861 study

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

## risc-v gcc toolchain build method    
* search baidupan, riscv-gcc-riscv-gcc-7.3.0.zip  
