1.安装git
sudo yum install git
2.查看版本
git --version
3.注册git账户
https://github.com
4.配置git
git config --global user.name "Yourname"
git config --global user.email example@exam.com
5.配置SSH公钥
	若之前配置过SSH，记得备份～/.SSH下的内容。然后
ssh-keygen -t rsa -C example@exam.com
回车默认。
6.配置公钥到github
vi ~/.SSH/vi id_rsa.pub
	复制内容，登录github，在右上方工具栏里找到Account Settings。在这个页面上有一个SSH Public Keys标签，选择Add another public key。Title可以随便填一个，Key就粘贴刚才的字符，提交。
7.测试SSH
ssh -T git@github.com
	输出：Hi Yourname! You've successfully authenticated, but GitHub does not provide shell access.

完成。


