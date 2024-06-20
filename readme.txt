test
Git是目前世界上最先进的分布式版本控制系统（没有之一）。
安装Git:
	安装完成后，还需要最后一步设置，在命令行输入：
	$ git config --global user.name "Your Name"
	$ git config --global user.email "email@example.com"
	注意git config命令的--global参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配	置，当然也可以对某个仓库指定不同的用户名和Email地址。
	使用git config --list命令就能看到你所有的设置
创建版本库:
	创建一个版本库非常简单，首先，选择一个合适的地方，创建一个空目录：

	$ mkdir learngit
	$ cd learngit
	$ pwd
	/Users/michael/learngit

	第二步，通过git init命令把这个目录变成Git可以管理的仓库：

	$ git init
	Initialized empty Git repository in /Users/michael/learngit/.git/

	现在我们编写一个readme.txt文件，内容如下：

	Git is a version control system.
	Git is free software.
	一定要放到learngit目录下（子目录也行），因为这是一个Git仓库，放到其他地方Git再厉害也找不到这	个文件。

	和把大象放到冰箱需要3步相比，把一个文件放到Git仓库只需要两步。

	第一步，用命令git add告诉Git，把文件添加到仓库：

	$ git add readme.txt
	执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

	第二步，用命令git commit告诉Git，把文件提交到仓库：

	$ git commit -m "wrote a readme file"
	[master (root-commit) eaadf4e] wrote a readme file
	 1 file changed, 2 insertions(+)
 	create mode 100644 readme.txt
	简单解释一下git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义	的，这样你就能从历史记录里方便地找到改动记录。

小结：
	现在总结一下今天学的两点内容：

	初始化一个Git仓库，使用git init命令。

	添加文件到Git仓库，分两步：

	使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	使用命令git commit -m <message>，完成。


