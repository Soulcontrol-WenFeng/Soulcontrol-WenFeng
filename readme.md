

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



# 2023-10-16  
10月13日的问题最后还是没有发现问题所在，由于是移植同事的工程，太多事件状态要看，并且同事用的IDF版本跟我不一样，也存在可能调用的函数是否一致等问题，故不再处理这个问题，转向新画板子IACC的测试。  

测试中发现，程序无法进行烧写，将电路上的RS485（该485为5V供电，数据口输出电压也为5V，而ESP32模组则为3.3V）芯片拆下后烧写正常。  

后续打算更换3.3V供电的485芯片测试看看。  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/d01dc3f2-cef1-45c9-92e6-43fbebbed088)




# 2023-11-21  
上周结束了为期三周的工厂重复性组装工作，昨日又重新回到公司来。在工厂这段时间的工作中，让我感受到了工厂同事的热情于乐观，我觉得他们才是真正的工人阶级，不抱怨，发挥主观能动性，将好的情绪传递给周围的人，希望他们能早日迎来双休。  



 也让我知道了在当今如此内卷的大背景下，想要躺平意味着要有一定程序的“卷”，也许就是老生常谈的先苦后甜吧。在此也深刻意识到了个人核心竞争力的重要性。  

 最近忙里偷闲搞了张小板子，想要趁着空闲时间做一个温湿度可显的小玩物，目前原理图和PCB已经更新到第二个版本，添加了气压计和姿态传感芯片MPU6050,也将第一版的电源芯片TPS563201DDCR替换成了AP2112K-3.3TRG1，减少了电源部分器件数量，使得小板子里能塞下更多东西。  
 -------------------  

 `版本一`  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/760deda5-e2a7-4918-be20-a6b6a69c7c3b)
 ![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/315202ea-757f-44df-b843-222160400280)
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/2d5a81e9-133b-4eac-af32-13746dfb5cc1)



`版本二（尚未走线）`  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/1409d8ac-fa05-4025-88c6-052c4b36780c)
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/6f2b7a34-1788-4428-8780-1989d999a715)




# 2023-11-22  
同事在对ESP32-C3模组进行烧写程序的时候，会出现一些欠压复位等不在意料之内的情况以及重新上电后仍然进入等待SPI下载的情况，如下：  
`rst:0xc (RTC_SW_CPU_RST),boot:0xf (SPI_FAST_FLASH_BOOT)`  
`SPIWP:0xee`  
`mode:DI0, clock div:1`  

`rst:0xf (BROWNOUT_RST), boot:0x1(SPI_DOWNLOAD_BOOT)`  
`wait spi download`  

`rst:0x1 (POWERON), boot:0xf (SPI_FAST_FLASH_BOOT)`  
`SPIWP:0xee`  

`rst:0xf(BROWNOUT_RST),boot:0x7(DOWNLOAD(USB/UART0/1))`  
`waiting for download`    

在以上情况当中，出现了  **rst:0xf (BROWNOUT_RST)**  ,  **boot:0xf (SPI_FAST_FLASH_BOOT)**  意味着欠压复位,  
如果是 **rst:0x1 (POWERON)**  意味着上电复位  




  # 2023-12-12 
  Thinking:  想根据自己卧室的增高架尺寸做一个桌面控制台，刚好可以嵌进增高架下面的空间，遮挡住后面的排查和电线，具有电脑主机开关机，温湿度等参数显示，旋钮调节音量等参数等功能，留有冗余接口   
  ------------------



#  2023-12-13  
Thinking：这段时间还想要做一个跟FOC相关的项目，或者跟无刷电机相关的项目，正好可以增进一下相关方面的知识。  
-------------------------------------------------------  
跟FOC相关的理论知识可以先行补充，此前有在知乎找到两个帖子，写得蛮精细，有一个是稚晖君做的关于FOC开源的项目，可做参考或者复刻。  
稚晖君：  
https://zhuanlan.zhihu.com/p/147659820   
其他：  
https://zhuanlan.zhihu.com/p/364247816  


# 2023-12-21  
记录：关于HT-IACC-S V1.02板子，红外发射的时候MCU会进入低压重启，拆掉IR05模块上面的四个红外发射头的其中2-3个的通路电阻（断开）问题解决，同时，新板子仍然有电源上电后的噪音问题，只不过是从旧板V1.01的滋滋滋声音变成了现在类似与继电器开断的嗒嗒嗒声。  
----------------------------------------  

今日任务一：阅读FOC控制的相关代码
--------------
**阅读的是稚晖君开源的Ctrl-FOC-Lite-fw版本的代码，有一份是基于STM32写的，但是文件结构和之前的看到的有点不一样，这份代码中有.project文件，应该可以在STM32CUBEIDE当中打开和编译，但是会报错，该工程代码文件结构如下**   
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/0596d394-5964-4c96-a11f-061abced5d08)  

**相较于以往的工程文件，只不过是多了几个文件夹，主体文件结构没有变化，所以编译不过可能是配置方面的问题**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/54cd971b-d0ff-450b-bb2b-7aedf726b11a)  

**我们查看IDE报错的信息：**    
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/afe6986a-26ac-4e63-b111-3a43eac1c661)  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/bbff49ce-6fde-4d2b-8172-359455e8d5fd)  

**这里面有个FATAL ERROR,找不到该文件，但很显然我还是索引到了该文件，这又是一个严重错误，排查中**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/346a67fe-9650-4914-a8c8-67b9da5acd7c)
**在UserApp和Platform等文件夹中的文件应该是C++的文件，后缀是.cpp**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/b21a273b-1402-4585-b7ca-705ce7d7580e)


**我们进入ide的添加头文件路径选项，将没有索引到的头文件添加到link路径当中**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/9c631fc0-a4f7-46f1-b8af-77bc034b2d94)
**重新build，这个时候我们发现，找不到.h文件的错误没有了，但是有新的错误出现，如下：**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/53081ed2-2ff3-46c7-a850-b6f7684cbaed)
**在console窗口我们可以看到这些错误的详情，我们发现，报错的路径中显示的是E 盘，但是我们的工程文件所在的workspace是在F盘，E盘中存在中文路径，可能有潜在的隐患，所以我决定删掉该工程文件，重新导入，这里我也意识到了错误的地方，一开始我是从下载的文件夹当中打开了工程文件，导致了工程并不在默认的WORKSPACE空间当中，这是一个低级错误**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/3d9d0a88-3673-4620-b65c-6a85ad8c6649)
**重新打开WORKSPACE路径，然后导入该工程，修改头文件路径，出现其他错误**  
![image](https://github.com/Soulcontrol-WenFeng/Soulcontrol-WenFeng/assets/74033919/3152a0b9-d474-4c4b-8a72-046c2a578c6a)

**在该份代码中，不是很确定UserApp当猴子那个的main.cpp会不会和Core/Src当中的main.c文件起冲突，并且二者都有一个mian()函数只不过一个是Main()**  











