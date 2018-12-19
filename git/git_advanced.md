# Practices and Workflows

## 1. To compare changes of local copy with remote
1. `git fetch origin` - Downloads remote code, but does not 
2. `git diff origin/Aditya -R` - Reverses the order with -R

## 2. Compare with previous commit & roll back
1. `git diff` - compares current updates with previous commit
2. `git reset --hard` - rollback to previous commit

## 3. Staging Workflow
1. `git diff`			# show the changes in the files(w.r.t prev. commit) before adding them to the staging index
2. stage the files
3. `git checkout file1`	# undo any changes made after the most recent staging of file1

### 3.a. Why does git have a staging-index?
1) Keep adding changes(which work well) in the staging index. If a change doesn't work well & you want to discard the changes, you can checkout the file or checkout all files with `git checkout *` to bring them to their **previous** staging state.
2) Split work into different commits -
	Say you came for a task x, but also found some formatting that could be improved. You could commit the fix in one commit & the formatting in another, to make it easier to review changes later.
- `git commit -a`	# If you want to forgo the staging-index

### 3.b. Commands used after staging -
- `git ls-files`		# shows the files currently in the staging-index
- `git rm file1 file2 ...`	# `mv`, `cp` are also supported

### 1.a. `git diff` usage
> **Summary: `git diff <default=HEAD> <default=current_code>`** \
where changes are from 1st arg to 2nd arg
1. `git diff HEAD origin/master` - changes required to convert **HEAD to origin/master**
2. `git diff origin/master`      - **origin/master to current code**(Not HEAD, if code is not commited)
3. `git diff`                    - **HEAD to current code** - useful when writing a commit message \
Note: `current code` is also called `working tree(unstaged changes)` \
*see examples in git help diff*

### 2.b. `git reset` usage
> **`git reset <default=HEAD>`**
1. `git reset --hard HEAD` OR `git reset --hard` - restore code to previous commit.
2. todo - w/o --hard?

# To Research & Resolve
- Using `git stash` to temporary save changes before changing the branch

- git remote update vs git fetch origin vs git fetch --all

- "git pull" works by itself, what is the need of "origin master"?

**get more tips from my keep notes**