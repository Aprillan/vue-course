使用git
配置：
	name  
			git config --global user.name "April Lan"
	email
			git config --global user.email "lan16626401915@163.com"
			
			
使用git：
	git status
		-- 查看当前仓库状态
	git init
		-- 初始化仓库
	
	刚刚添加到项目中的文件属于未跟踪状态：
		未跟踪 --->  暂存
			git add <filename> 将文件切换到暂存的状态
			git add * 将所有已修改（未跟踪）的文件暂存
		暂存 ---> 未修改
			git commit -m "xxxx"将暂存的文件存储到仓库中
			git commit -a -m "xxxx" 提交所有已修改的文件（未跟踪的文件不会提交）
		未修改 ---> 修改
			修改代码后， 文件会变为修改状态

 常用命令
 
 1.重置文件
    git restore <filename>  恢复文件
	
	git restore --staged <filename>  取消暂存状态

 2. 删除文件
	git rm <filename>  删除文件
	
	git rm <filename> -f  强制删除 

 3. 移动文件
	git mv from to  移动文件 重命名文件
 
			
 分支branch

	git在存储文件时，每一次代码提交都会创建一个与之对应的节点
	git就是通过一个一个的节点来记录代码的状态
	节点会构成一个树状结构，树状结构就意味着这个树会存在分支
	默认情况下仓库只有一个分支，命名为master（main）
	
	在使用git时，可以创建多个分支，分支与分支之间相互独立，
	在一个分支上修改代码时不会影响其它分支
	
	1.查看当前分支
		git branch 
	2. 创建新分支
		git branch <branchname>
	3. 删除分支
		git branch -d <branchname>
	4. 切换分支
		git switch <branchname>
	5. 创建并切换分支
		git switch -c <branchname>
	
	
	在开发中都是在自己的分支上编写代码，
	代码编写完成后，再将自己的合并到主分支中
	
	在开发中除了通过merge来合并分支外，还可以通过变基(rebase)来完成分支的合并
	
	
	通过merge合并分支时， 在提交记录中会将所有的分支创建和分支合并的过程，
	全部都显示出来，当项目比较复杂， 开发过程比较波折时，
	我们必须要反复创建，合并， 删除分支，
	这样一来将会使得我们代码的提交记录变得极为混乱，
	
	变基原理：
		1.当发起变基时，git会找到两条分支最近的共同祖先（最近的交点）
		
		2. 对比当前分支相对于祖先的历史提交，并且将它们的不同提取出来存储到一个临时文件中
		
		3. 将当前部分指向目标的基底
		
		4. 以当前基底开始，重新执行历史操作
		
	rebase 和 merge 对于合并分支来说最终的结果是一样的，
	但是rebase 会使得代码的提交记录更整洁更清晰
	
	注意：大部分情况下，rebase和merge可以互换，
		但是如果分支已经提交给远程仓库了，那么这时尽量不要使用rebase
		
	远程仓库（remote）
	
	目前我们对于git所有操作都是在本地进行的， 在开发中显然不能这样，
	这是我们就需要一个远程1git仓库，远程的git仓库和本地的本质上没有什么区别
	不同点在于，远程仓库（remote）可以被多人同时访问使用， 方便我们协同开发
	在实际开发中， git的服务器通常由公司搭建内部使用或者购买一些公共的私有git服务器
	
	学习阶段，直接使用开放的公共git仓库目前常用的库有两个：GitHub，Gitee（码云）
	
	将本地库上传到git：
	
	git remote add origin https://github.com/Aprillan/Git-demo.git
	# git remote add <remote name> <url> 
	
	git branch -M main
	# 修改分支的名字为main
	
	git push -u origin main
	# git push 将代码上传到服务器上