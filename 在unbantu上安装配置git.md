- 更新软件源
命令
sudo add-apt-respository ppa:git-core/ppa
sudo apt-get update
- 安装git
sudo apt-get install git

- 检查安装是否成功
git --version

- 设置git

1)设置用户名和email
git config --global user.name "cxspace"
git config --global user.email "442961832@qq.com"

- 为github帐号添加ssh keys

1)创建ssh key

ssh-keygen -t rsa -C "442961832@qq.com"
连续三次回车
（2）Copy SSH Key

然后用vim打开该文件，id_rsa.pub文件内的内容，粘帖到github帐号管理的添加SSH key界面中。

vim ~/.ssh/id_rsa.pub

（3）添加到GitHub

登录github-> Accounting settings图标-> SSH key-> Add SSH key-> 填写SSH key的名称（可以起一个自己容易区分的），然后将拷贝的~/.ssh/id_rsa.pub文件内容粘帖-> add key”按钮添加。

（4）测试

ssh -T git@github.com

4. 为GitHub上的Repository提交修改

（1）git clone已存在GitHub上的Repository。（在新建的~/MyTestFolder目录中）

git clone https://github.com/zhchnchn/ZhchnchnTest.git

（2）修改一个文件，然后提交

vim README.md
git status
git add README.md
git status
git commit -m "Edit by WorkUbuntu 1204"
git status
git remote add origin https://github.com/zhchnchn/ZhchnchnTest.git

这时会报错误：

fatal: remote origin already exists.

解决办法【3】：

$ git remote rm origin

然后再次执行 git remote add origin https://github.com/zhchnchn/ZhchnchnTest.git

（3）之后，需要将修改push到GitHub上

git push -u origin master

执行该条命令后，会要求输入GitHub账户的用户名和密码。

（4）提交完成后，查看GitHub上的Repository，会发现内容修改成功。
