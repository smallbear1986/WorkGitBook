## 在Windows下使用dryrun
1.下载Ruby和Devkit，http://rubyinstaller.org/downloads/，选择自己需要的版本，
  先安装Ruby，我是用的.exe安装的，建议以管理员身份运行
2.记得设置ruby的环境变量。记住，设置后，需要重新开启cmd。
3.执行ruby dk.rb init，然后在Devkit的目录下会生成config.yml文件，
打开文件将你Ruby的安装路径填写进去，比如:- E:\Ruby23-x64，注意“-”符号
然后我们在执行ruby dk.rb install命令
4.安装完成后在执行gem install rdiscount --source http://rubygems.org
5.gem install dryrun --source http://rubygems.org
6.dryrun https://github.com/cesarferreira/android-helloworld



手动下载gradle
1.在Android Studio中取消下载（不过貌似有个bug，取消不了，
那就直接在运行studio.sh的终端中按Ctrl + C 退出Android Studio）。
将gradle-1.10-bin.zip.part移除，把自己下载的gradle-1.10-bin.zip复制到这个目录。
2.然后在终端中输入gradle -v


将Eclipse工程导入Android Studio
直接找到原有的Eclipse工程
单一工程直接导入即可。
有库工程的需要注意，导入一定要指向主工程，而不是整个项目的目录。指向项目目录是无法进行转换的。


>请在此记录你的学习笔记
