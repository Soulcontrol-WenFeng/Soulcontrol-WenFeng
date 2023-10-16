

# 2023-10-09  
关键词：NAS、循环缓冲、旋转矩阵、cubeide dark theme plug-in、GitHub link、PCB Backup、some stupid GitHub items   
--------------------------  
今日学习效率低下，真是辛苦自己了  





# 2023-10-10  
关键词：CUBEIDE DARK THEME、ECLIPSE MARKETPLACE……  
--------
描述：在公司电脑上下载并且使用了CUBE IDE，一开始软件的背景为白色，很刺眼，后来在Eclipse Marketplace中下载dark theme插件更改成功。但是在个人PC上重复步骤却一直出错，下载到46%左右的时候会报错，之前公司电脑也会出现该错误但是查看之前的工作日志发现是有解决的，但是复刻步骤在PC上却没有成功   
**公司电脑的当前IDE界面:**
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/c6614e58-6c2b-4ef3-a203-ab2bf3215b9c)
**查看曾经解决的工作日志：**
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/7c3935af-23a9-468f-90e3-a9638481e167)



# 2023-10-11  
今天还是尝试从官网下载cubeide的最新版本，竟然下载成功了，传回QQ晚上回去在PC上面再试一下   
`code`  
`printf("Hi World\r\n");`  
<font size=7>官网链接</font>：  
```  
https://www.st.com/zh/development-tools/stm32cubeide.html#st-get-software  
```
<font color=yellow>跳转链接</font>  
  **[CUBEIDEGET](https://www.st.com/zh/development-tools/stm32cubeide.html#st-get-software)**   
<https://www.st.com/zh/development-tools/stm32cubeide.html#st-get-software>  

![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/ce98ffc3-dd82-464a-a9df-804b4ce72e32)  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/e2b9432a-ffbc-4a0f-b464-b4de22675cdb)  
官网上的最新版本为1.13.2，公司电脑上的为1.12.1，可能是版本不够新的问题，PC上的1.5.0software升级每次也都不成功  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/e80a8425-4149-49b5-9c54-498028ddf473)  

回到住所后将官网下载的1.13.2版本下载在PC上，下载成功后软件默认为黑色主题背景，以为是已经下载好了DARK THEME插件，点进去发现是软件自带的黑色设置，不过这个版本的黑色背景确实还可以，但是代码高亮的部分比较一般，可以说有点清爽，于是又下载了一遍DARK THEME插件，这回成功下载并且重启，值得注意的是官网下载的这个版本需要登陆你的个人账号才能进行设备支持包等一系列插件或者软件的下载，以下：  
![KQ) TS`BY@I$4 B WNT2)I](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/984f9903-d74c-4495-bd97-e4a1c86b4b12)



# 2023-10-12


# 2023-10-13  
关键词：Eclipse、乱码、UFT-8、代码移植、CMakelist  
--------------

问题：今天在移植同事的一个工程（基于ESP32模组的代码）的时候编译不过，一般编译到一半就出错，显示某文件中索引不到某变量或者某定义（由于失败工程已经删除此处不放截图）。这里猜测可能是因为某些包含的头文件没有被索引到。同事用于代码编辑的工具是notepad++，编译的平台是乐鑫提供的ESP-IDF-CMD,不过他的版本为五点多，我电脑上面的则是4.4，可能由于版本不一样导致无法编译。但是在ESP提供的Espressif-IDE中编译也仍然报错，如下：  

![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/1c0e428f-464e-4456-9136-4e564c5908b6)  

主要为两种错误：  
`1、implicit declaration of function ……，did you mean  ……（隐式声明）`
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/59e500f5-be72-4684-bdca-9ef3bfb2e976)  

`2、symbol '……‘ could not be resolved(符号无法解析)`  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/a2b8b28b-86a3-4604-abc7-5047cc8aba4e)

根据我以往的经验，出现该两种错误有可能是其他错误造成的，比如头文件索引问题，或者是cmakelist里面的头文件和源文件路径问题，在该工程当中，很容易就可以发现符号CONFIG_I2C_MASTER_PORT等以下列I2C相关定义没有找到，而在main文件中却仍被调用，有可能同事发给我的工程少了一些文件，也有可能是某处的编译开关被关掉导致无法索引。  

针对第问题2，我们可以产看错误符号所在的位置，我们发现，代码段有一个编译开关，而很显然，在该工程中此编译开关应该是关闭的，因为没有I2C驱动，以下：  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/b23ecb1a-6d8e-44a2-b054-3b1c9c106a8d)
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/58f8cc1b-3a95-4231-a38c-553cdb377917)

然后注释掉，重新编译，又开始报莫名其妙的错误，于是我决定，建立新工程，这次我只拷贝.c和.h文件，可能有个sdkconfig的文件会影响到，所以只拷贝如下几个：    
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/6222983f-e9e6-4c22-a581-2a0514500dd4)



