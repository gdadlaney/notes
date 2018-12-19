1. Install git  
`sudo apt-get install git`

2. Check for name  
`git config --global user.name`

3. Configure your name  
`git config --global user.name "Your name"`

4. Check for mail  
`git config --global user.email`

5. Configure email  
`git config --global user.email "email@example.com"`

6. Create a new directory with name of your choice

7. cd into that directory

8. Run following commands
	- `git clone https://github.com/gdadlaney/Data-Exchange-Platform.git` \
	OR the mext 3 commands
	- `git init`
	- `git remote add origin  https://gitlab.com/gdadlaney/Data-Exchange-Platform.git`	# "origin" is your remote_name (part of .git/refs/remotes/)
	- `git pull origin master`
	- `git remote -v`	# lets you check the origin urls
	
9. After changing any file at the end of the day run following commands
	- `git add .`						# Add new/updated files to staging index
	- `git commit -m "message"`			# Always add an informative message
	- `git pull origin master`			# **Always pull updates from remote before a push**, else remote won't remain stable
	- `git push origin master`

10. Branching
	- `git checkout -b new_branch`		# create a new branch & switch to it
	- `git checkout master`				# switch to any branch
	- `git branch` 						# show all branches in current local repo
	
	- `git checkout master && git merge new_branch`	# merge new_branch with master branch
	- `git branch -d new_branch`			# delete a branch after it has been merged ( -D to remove a branch w/o merging )

## Workflow for making changes to code
1. pull the branch(you want to change, say `master`) from remote
2. create a new branch, say `branch1`
3. commit
4. pull `branch1`, just in case someone had made changes in the branch
5. push `branch1`
6. Create a `Pull Request` on github

### Add individual files to staging/commit
- `git add file1 [file2 ...]`
- `git commit [file1 ...] -m "..."`


> Read more about pulling, pushing from a remote repo & merge_conflicts:  
https://stackoverflow.com/questions/5601931/best-and-safest-way-to-merge-a-git-branch-into-master

### Other Commands - 
- `git help <command>` 	OR 		`git help -a`
- `git log` - to see the history of commits