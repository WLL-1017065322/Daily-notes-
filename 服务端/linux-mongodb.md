#### 路径设置:

1、直接在命令行中设置PATH
\# PATH=$PATH:/usr/local/apache/bin
使用这种方法,只对当前会话有效，也就是说每当登出或注销系统以后，PATH设置就会失效。

2、在profile中设置PATH
\# vi /etc/profile
找到export行，在下面新增加一行，内容为：export PATH=$PATH:/usr/local/apache/bin。
注：＝ 等号两边不能有任何空格。这种方法最好,除非手动强制修改PATH的值,否则将不会被改变。
编辑/etc/profile后PATH的修改不会立马生效，如果需要立即生效的话，可以执行# source profile命令。

3、在当前用户的profile中设置PATH
\# vi ~/.bash_profile
修改PATH行,把/usr/local/apache/bin添加进去,如：PATH=$PATH:$HOME/bin:/usr/local/apache/bin。
\# source ~/.bash_profile
让这次的修改生效。
注：这种方法只对当前用户起作用的,其他用户该修改无效。

4======2019.7.29使用该方法:修改文件root/.bashrc   home/admin/.bashrc

/etc/profile 对应 sh
~/.bashrc 对应 bash
bash 先找 ~/.bashrc ，如果没有才去找/etc/profile ，算是保持对sh的一致



#### 后台运行:

/usr/local/mongodb/bin/mongod  --fork --dbpath=/usr/local/mongodb/data  --logpath=/usr/local/mongodb/data/logs/mongodb.log  --logappend



#### 报错:

1,输入mongod,报错:

![1564391924118](assets/1564391924118.png)



解决方案: