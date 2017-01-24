### Eclipse Memory Analyzer tool(MAT)使用

>1.要用MAT工具分析内存泄露的第一步就是获取Heap Dump文件.  
>2.在DDMS工具。选中要查看的进程后，点击”Dump HPROF file”按钮，然后使用platform-tools
中的hprof-conv.exe将刚才生成的hprof文件转换成MAT能够识别的hprof文件。  
3.select * from instanceof android.app.Activity
4.选择“exclude weak/soft references”筛选出除了软引用和弱引用之外的对象，也就是强引用了!
