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


>请在此记录你的学习笔记