Android 运行时内存分析
==========================
可使用smaps文件进行分析<br>

1.路径在:<br>
`/proc/$pid/smaps`<br>
pid 可通过：<br>
`adb shell dumpsys meminfo <package_name>`<br>
 来获取<br>
 
2.以下图显示为例，说明其各字段的意义（摘取`https://zhidao.baidu.com/question/2077299873435988108.html`）<br>
![image](https://github.com/Cloud-lys/Android--analysis-of-run-time-memory-ratio/blob/master/draw/smps.jpg)<br>

1）、08048000-080bc000:地址空间的开始地址 - 结束地址 <br>

2）、r-xp属性:前三个是rwx（读、写、可执行）,如果没有相应的权限则为“-”。最后一个可以是p或者s(p表示私有，s表示共享) 。<br>

3）、00000000：偏移量，如果这段内存是从文件里映射过来的，则偏移量为这段内容在文件中的偏移量。如果不是从文件里面映射过来的则为0. <br>

4）、03:02：文件所在设备的主设备号和子设备号<br>

5）、13130：文件号，即/bin/bash的文件号<br>

5）、/bin/bash：文件名<br>

7)、Rss：Resident Set Size 实际使用物理内存（包含共享库占用的内存） <br>

Rss的大小=Shared_Clean+Shared_Dirty+Private_Clean+Private_Dirty <br>

8）、Pss：实际使用的物理内存（按比例包含共享库占用的内存）。比如四个进程共享同一个占内存1000MB的共享库，每个进程算进250MB在Pss。 <br>

9）、Shared_Clean 、 Shared_Dirty 、 Private_Clean、 Private_Dirty：<br>

（shared/private）共享和私有 <br>

一个页的clean字段表示没有更改此页，当发生换页时不用写回。dirty表示更改了此页，当发生换页时要写回磁盘。此处这四个值是遍历页表中各个页后得到的。 <br>
