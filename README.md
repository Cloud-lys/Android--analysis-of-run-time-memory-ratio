Android 运行时内存分析
==========================
可使用smaps文件进行分析<br>

1.路径在:<br>
`/proc/$pid/smaps`<br>
pid 可通过：<br>
`adb shell dumpsys meminfo <package_name>`<br>
 来获取<br>
 
2.以下图显示为例，说明其各字段的意义（摘取`https://zhidao.baidu.com/question/2077299873435988108.html`）<br>

