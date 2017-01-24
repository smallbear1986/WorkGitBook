### ClassyShark
>1.下载地址：https://github.com/google/android-classyshark/releases  
>2.使用方法  
````
2.1打开apk文件java -jar ClassyShark.jar -open <YOUR_APK.apk>  
2.2将生成的所有数据导出到文本文件里java -jar ClassyShark.jar -dump <BINARY_FILE>  
2.3将指定类生成的文件导出到文本文件里java -jar ClassyShark.jar -dump <BINARY_FILE> <FULLY_QUALIFIED_CLASS_NAME>  
2.4打开ClassyShark，在GUI界面展示某特定的类
java -jar ClassyShark.jar -open <BINARY_FILE> <FULLY_QUALIFIED_CLASS_NAME>  
2.5检测APKjava -jar ClassyShark.jar -inspect <YOUR_APK.apk>  
2.6导出所有的字符串 java -jar ClassyShark.jar -stringdump <YOUR_APK.apk>
````

### apktool反编译apk
1.xml文件反编译（用apktool）   
2.dex2jar、enjarify、jadx（获取源文件jar包）
  jadx：https://github.com/skylot/jadx/releases  
  直接使用jadx可以查看apk反编译代码
3.JD-GUI （反编译源文件jar包查看源代码）
