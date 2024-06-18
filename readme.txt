test
https://www.liaoxuefeng.com/wiki/896043488029600/896827951938304
廖雪峰的官方网站（Git教程）
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

时光穿梭机：
	git status命令可以让我们时刻掌握仓库当前的状态
	git diff顾名思义就是查看difference，显示的格式正是Unix通用的diff格式。如：
	$ git diff readme.txt 
	diff --git a/readme.txt b/readme.txt
	index 46d49bf..9247db6 100644
	--- a/readme.txt
	+++ b/readme.txt
	@@ -1,2 +1,2 @@
	-Git is a version control system.
	+Git is a distributed version control system.
	 Git is free software.

小结：
	要随时掌握工作区的状态，使用git status命令。

	如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

版本回退：
	Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为	commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把	几个月的工作成果全部丢失。
	git log命令显示从最近到最远的提交日志。
	版本回退，首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交	1094adb...（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然		往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
	使用git reset命令：

	$ git reset --hard HEAD^
	HEAD is now at e475afc add distributed
	--hard参数有啥意义？这个后面再讲，现在你先放心使用。

	现在，你回退到了某个版本，关掉了电脑，第二天早上就后悔了，想恢复到新版本怎么办？找不到新版本	的commit id怎么办？

	在Git中，总是有后悔药可以吃的。当你用$ git reset --hard HEAD^回退到add distributed版本时，再	想恢复到append GPL，就必须找到append GPL的commit id。Git提供了一个命令git reflog用来记录你的每一	次命令：

	$ git reflog
	e475afc HEAD@{1}: reset: moving to HEAD^
	1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
	e475afc HEAD@{3}: commit: add distributed
	eaadf4e HEAD@{4}: commit (initial): wrote a readme file
	终于舒了口气，从输出可知，append GPL的commit id是1094adb，现在，你又可以乘坐时光机回到未来了。

小结：
	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard co	mmit_id。

	穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

	要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。



