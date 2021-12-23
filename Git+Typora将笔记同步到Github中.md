# Git+Typora将笔记同步到Github中

### 1.准备软件GIt

### 2.新建一个Github仓库，用来保存笔记

### 3.配置名字和邮箱

1. 打开Git软件，输入命令：

- **git config --global user.name "Your Name"**

- **git config --global user.email "email@example.com"**

2. 使用**git config --global --list**查看是否配置成功

![image-20211223220032904](C:\Users\19778\AppData\Roaming\Typora\typora-user-images\image-20211223220032904.png)

### 4.生成密钥与Github进行连接

1. 在Git Bash中输入命令**ssh-keygen -t rsa -C "email@example.com"**，按三下回车。
2. 如果运行成功，在 **C:\Users\Administrator\.ssh**目录下会生成三个文件，其中**id_rsa.pub**中存放的就是密钥。
3. 在Github中点击头像-->Settings-->SSH and GPG keys-->New SSH key。将名称和密钥填入。

![image-20211223220826598](C:\Users\19778\AppData\Roaming\Typora\typora-user-images\image-20211223220826598.png)

![image-20211223220942574](C:\Users\19778\AppData\Roaming\Typora\typora-user-images\image-20211223220942574.png)

### 5.将本地文件上传到Github仓库

1. 在你想要上传的目录里面打开Git，输入**git init**,将目录初始化成本地仓库，初始化成功后你会发现项目里多了一个隐藏文件夹.git
2. **git add 文件名或目录**，如果想上传所有文件可以用**git add .**
3. **git commit -m** "描述"。
4. **git remote add origin 你的仓库链接**，此命令将本地仓库与你的远程仓库进行连接。
5. **git push -u origin master**，将本地文件push到远程仓库，此时在Github上就可以看到上传的文件。