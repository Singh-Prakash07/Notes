First we will see how to push local file on github. Then we will see how to use git to track our project version.

### git hub

//This is how we push our locally git repo into git hub repo(github)
1. In github at topmost we click on "+" icon and select "New repository"
2. Enter repo name,select public/prvate,could select 'add a README file'.
3. Then we have two option either create new or push from local.

### push on github
1. open project in terminal and use command.( all are bash command).
```
git init 
```
+ open project in terminal this command creates a hidden .git folder that tracks all the changes to your files.

2. Add all of your project files to the staging area.
```
git add . 
```
This tells Git which files you want to include in your first commit. The . means "all files."

3. Create your first commit.
```
git commit -m "Initial commit"
```
This saves a snapshot of the files you just added. The text inside the quotes is your commit message.

4. Connect your local repository to the remote GitHub repository.
```
git remote add origin <URL_from_GitHub>(https://...).
```
origin is a shorthand name for the remote URL. You'll get the specific URL from GitHub after creating a new repo.
we get url of github repo created.

5. Push your local main branch to the remote repository.
```
git push -u origin main
```
This is the final and most crucial step. It sends your local commits to GitHub. The -u flag sets the upstream, so future pushes can be done with just git push.
6.to verify if your remote connection (the URL) has been set up correctly. You can confirm everything looks good!
```
git remote -v
```
> [!Note]
> An error often happen if you created a repository on GitHub with a README file or a license, but you haven't pulled those files down to your local machine yet.

+ To fix this, you need to pull the changes from the remote repository before you can push your own work.
1. Pull the changes from the remote repository: This command will fetch the latest changes from the remote main branch and merge them into your local main branch.

Bash
git pull origin main
You might see a message about merging, which is normal. Git will automatically try to combine the files.

### push pull 
1. After adding your local repo on github each time you do the changes in your local repo
	you need to do commit for local git then after you use command(git push origin master)
	to push locally changed`project to show that changes on github.
2. And if your collaborator done changes then you need to pull from github before to further changes
	and you use command (git pull origin master) only then that change from git show on your local project.

### clone

	// 1.How to make clone of github repo in local and make changes.
	// 2.git clone https://github.com/..........
	// 3.line 2 code we will get from github's repo
	// 4.code-> cd repo_name/
	// 5.ls ("to get list of all files).
	// 6.vim README.md   (it opens the file in which u want to change in terminal itself	
	// 7.after file opened, we need to press "i" to start editing
	// 8. after modify in file to save and exit we press(a.escape->:->w->q
	// 9.cat README.md it will show the changes came in that file. 	


initially when you install git you need to set or config. name and email of user

### how to see version of git in terminal
		git --version
### how to set name and email of user
```	
 	git config --global user.name "prakash singh"
	git config --global user.email "prakashgolusingh2020@gmail.com"
```
### how you see which email id set in your git
```
git config --global user.email
result --->	prakashgolusingh2020@gmial.com
```
### how edit email and name
	`git config --global --edit`
+ this will open vim edit where you can set name and email.
+ for edit you begin with pressing "i" then start with editing.
+ after edited you need to press "esc(button) : wq" button to save and exit.

### what actually we do in git	
1. Initialize git into a directory-->
2. Working directory-->(git add)--> 
3. staging area -->
4. (git commit)--> c.repository

### initialize git into a directory(git init)
	
+ Go to the folder which you need to track using git then open it in terminal   
+ Then we need to write a command "git init"
+ An empty git repository initialized in that directory
+ If we use "ls" then we can't see that .git file as it is hidden
+ We use "ls -a" to see that hidden file.
+ Now we need to create a file to add or commit into git.

### git status
	
+ It shows the status of each file that in the git repository that is
+  A file when and what modification done in a file
+ either that file is not tackble
+ About whether that file is in staging area or already commited, etc.
+ It should be noted that after creating each new file we need to..
+ add it into staging area then commit to track it.

8.================================git add================================

// when we create a file in git repository,it still can't be tacked by git.
// If we use command "git status" it will say file not trackable.
// so we use command "git add file_name" to add it into staging area
// Ex -> git add "sum two no.java"
// staging area where we use to hold the file before commit it.
// Now "git status" say ready to commit that file.
// we use "git add ." to add all files altogher to pass in staging area.

9.===========================git commit -m(m= "message") "=============================

	// To push a file from staging area to commited.
	// m means message and it should be meaningfull.
	// In double quote we write about the changes we have done in file.
	// like first time after created we generally..
	   write->  git commit "initial commit"
	// With same code writing once commit all the file of staging area.

10.========================git log==========================================
	
	// This command use to see all commit of a file 
	// It tell about everything like when,who,what change done it that file.

11.=========================git checkout <hashcode of commited file>==========

	// using "git log" we get all file with all stage of changes with time.

12.=========================git branch branch_name===========================

	// it create a new branch with all previous file. 
	// creating new branch will not affect the master branch of any previous branch.

13.=========================merge============================================

	// If you are at branch with created new file then if you want to 
	// merge your current change with previous one you use merge
	// code-> git merge current_branch_name.
	// Then -> git checkout newly_created_branch_name to enter in that new branch

14.=========================== git checkout -b new_branch_name========

	// It create new branch and enter in it automatically 
	// It does same work that code written above.

15.=======================touch .gitignore=========================================

	//this is .gitignore files in this file we write the name of all file which.
	// we wanna not include in git.
	//  and now other user wouldn't able to get it and git ignore that folder.

