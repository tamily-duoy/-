# -
系统各种配置的文档
--------------------------配置Git-----------------------------------------
在打开的GIt Bash中输入以下命令（用户和邮箱为你github注册的账号和邮箱）
$ git config --global user.name "用户名"
$ git config --global user.email "邮箱@qq.com"

生成秘钥：
$ ssh-keygen -t rsa -C "邮箱@qq.com"
3次回车

检查秘钥是否生成
$ cd ~/.ssh
$ ls
检查：是否存在2个文件：id_rsa  id_rsa.pub

-----------------------------配置GitHub ssh key------------------------------------
登录GitHub个人账号：
setting》SSH and GPG keys》new SSH key》add SSH key。
仓库名：本地文件夹名
地址：ssh-rsa ...... 邮箱@qq.com
     注：地址从C:\Users\Administrator\.ssh中复制id_rsa.pub中全文粘贴;或者直接从vi命令打开id_rsa.pub文件
     
------------------------------创建本地仓库-----------------------------------
进入本地文件夹：$ cd f:
本地仓库文件夹: $ cd pycharm/pyfile/
初始化本地仓库：$ git init
      注：初始化成功后，项目增加隐藏文件夹 .git
      
将所有文件添加到仓库：$ git add .
执行提交命令： $ git commit -m "此处添加注释文字"

------------------------------关联本地仓库到GitHub-----------------------------------
创建GitHub文件夹：pyfile
      注：尽量与本地仓库问价夹名保持一致；创建成功后，出现仓库地址---ssh地址
 
------------------------------上传本地项目到GitHub-----------------------------------
$ git remote rm origin
增加分支： $ git remote add origin git@github.com:（github帐号名）/（项目名）.git  
          $ git remote add origin git@github.com:tamily-duoy/pyfile.git 
 代码合并：$ git pull --rebase origin master
      注：合并成功后，本地代码库中多了README.md文件
 上传本地代码：$ git push -u origin master
      注：请输入--用户名：用户名；  密码：tokens的密码
 
 ---完成------
 
 ------------------------------常见失败原因-----------------------------------
 问题1：上传代码时，用户名或密码错误
 解决1：控制面板》用户账户》凭据管理》普通凭据》添加：
        网络地址：git:https://github.com 或git:https://git.oschina.net
        用户名：Personal access tokens
        密码：tokens的密码
        GitHub的Personal access tokens配置：设置》开发者设置》Personal access tokens》新增
 问题2：执行$ git add . 时，报错：warning: LF will be replaced by CRLF in XXXXXXXXXXXXXX.
 解决2：配置$ git config core.autocrlf false 后，再add时，就不报错了
 
 问题3：错误提示：fatal: remote origin already exists.
 解决3：先输入$ git remote rm origin
       再输入$ git remote add origin git@github.com:（github帐号名）/（项目名）.git
       如果输入$ git remote rm origin --error: Could not remove config section 'remote.origin'.     
       解决3：修改gitconfig文件：github的安装路径》gitconfig文件》删掉行：[remote "origin"]
  
  问题4：IP问题：Warning: Permanently added 'github.com,192.30.253.112' (RSA) to the list of know in hosts.
  解决4：$ vi /etc/hosts 》192.30.253.113  github.com
   
  








