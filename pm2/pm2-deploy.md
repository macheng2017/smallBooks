为什么要用pm2?

以前部署项目的方式 

	1. 从github上下载
	2. 打包后通过ssh 或者FTP上传到服务器,
	3. 在服务器上找到并解压缩,放到相应的文件夹
	4. 使用npm install 安装依赖 以及编译css 压缩js文件等等
	5. 删除压缩包以及设置文件夹权限 
	6. 运行项目,如果报错
	7. 切换文件夹查看日志文件
	8. 在本地修改然后循环步骤2-7直到完美运行

        ....

增加一个新功能后者一行代码
        重复1-8

使用pm2以后的部署方式,当所有配置完成后三行命令

	1. git push                                                                  推送到github或者码云上
	2. pm2 deploy ecosystem.json production setup     第一次从github上拉取到服务器
	3. pm2 deploy ecosystem.json production               部署并运行 看到 success   
	4. 如果报错使用pm2 logs 重复1,3


增加一个新功能后者一行代码

	1. git push 

       2. pm2 deploy ecosystem.json production 


看到pm2 部署你的项目是不是很幸福,以前的工作方式简直是在透支生命啊，不到可以提高幸福指数，还可以拯救生命。

步骤

	1. 在服务器和本地创建密钥
	2. 安装node.js pm2
	3. 在github上建立仓库
	4. 使用密钥配置服务器,本地,github三者无密码登录
	5. 配置pm2 的部署配置文件



提问提问提问



    pm2最原始形态应该就是一个shell脚本，本来一个程序员2个小时就能完成的部署，他却花费20个小时研究出来一个自动化部署的脚本，然后上传到社区，参考xxx漫画



在本地和服务器创建密钥
    note: 

	* 至于说ssh秘钥登录原理自行搜索,本文关注点在于实现步骤

	* 需要在本地电脑和服务器上装好git Bash(Mac系统没用过,好像不用get也行,反正有个终端能执行shell就行)
	* 需要在本地和服务器都要执行一边创建过程,创建过程都是一样的
	* 检查电脑中是否已经存在ssh key   ll -a ~/.ssh 如果现实不存在文件或文件夹则继续,否则可以跳过也可以重新生成一次(会覆盖掉以前的ssh key文件)



	1. 先在本地创建 ssh key

        ssh-keygen -t rsa -b 4096 -C "邮箱地址"
        然后不需要输入密码,直接回车回车(否则会很麻烦)
        检查 cd ~ 账户下 ~/.ssh文件夹下是否多了3个文件
          ~/.ssh/id_rsa            私钥
          ~/.ssh/id_rsa.pub     公钥
          ~/.ssh/know_hosts    主机记录,第一次登陆之后主机信息,当你敲yes之后会被记录到这个文件
        ![image](http://github.com/macheng2017/smallBooks/raw/master/images/ssh_show.png)

	1. 将ssh key 加入代理

           
        eval $(ssh-agent -s)     启动 ssh-agent
        ssh-add ~/.ssh/id_rsa  将私钥加入代理中
        
       3. 将公钥添加到github上
             使用 cat ~/.ssh/id_rsa.pub   查看并复制公钥
            登陆你的github账户>头像下找到setttings > SSH >粘贴
 
       4. 测试下是否配置成功
        ssh -T git@github.com

        
        
        好了已经打通了,本地与GitHub之间的无密码登录了

        服务器使用相同的命令在子账号下使用如下命令,不要在root账户下操作
        




  https://help.github.com/articles/connecting-to-github-with-ssh/






