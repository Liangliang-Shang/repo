# GIT
* A free and open source distributed version control system(VCS)
# Version
```
@Liangliang-Shang ➜ ~ $ git -v
git version 2.42.1
@Liangliang-Shang ➜ ~ $ git --version
git version 2.42.1
@Liangliang-Shang ➜ ~ $ git version
git version 2.42.1
```
# Help
```
@Liangliang-Shang ➜ ~ $ git help
usage: git [-v | --version] [-h | --help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           [--config-env=<name>=<envvar>] <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone     Clone a repository into a new directory
   init      Create an empty Git repository or reinitialize an existing one
...
```
# Config
* `git config --global user.name "Liangliang"`
* `git config --global user.email "liangliang.shang@icloud.com"`
# Local Repository
## Init
```
@Liangliang-Shang ➜ ~ $ mkdir test && cd test

@Liangliang-Shang ➜ ~/test $ git status			           # keep tracking
fatal: not a git repository (or any of the parent directories): .git

@Liangliang-Shang ➜ ~/test $ git init .			           # init a repo: ~/test
Initialized empty Git repository in /home/codespace/test/.git/

@Liangliang-Shang ➜ ~/test (main) $ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
## Config
```
@Liangliang-Shang ➜ ~/test (main) $ git config --local core.editor vim

@Liangliang-Shang ➜ ~/test (main) $ git config --list --show-origin --show-scope
system  file:/etc/gitconfig     init.defaultbranch=main
system  file:/etc/gitconfig     filter.lfs.smudge=git-lfs smudge -- %f
system  file:/etc/gitconfig     filter.lfs.process=git-lfs filter-process
system  file:/etc/gitconfig     filter.lfs.required=true
system  file:/etc/gitconfig     filter.lfs.clean=git-lfs clean -- %f
global  file:/home/codespace/.gitconfig user.name=Liangliang
global  file:/home/codespace/.gitconfig user.email=liangliang.shang@icloud.com
local   file:.git/config        core.repositoryformatversion=0
local   file:.git/config        core.filemode=true
local   file:.git/config        core.bare=false
local   file:.git/config        core.logallrefupdates=true
local   file:.git/config        core.editor=vim
```
## Working Directory
## Index/Staging Area
## Repository
![](https://pic4.zhimg.com/80/v2-a933cd4bb34672899ffd5a30cccdce03_720w.webp)
## File Status
* **`Untracked`**
  ```bash
	@Liangliang-Shang ➜ ~/test (main) $ git log
	fatal: your current branch 'main' does not have any commits yet

	@Liangliang-Shang ➜ ~/test (main) $ git reflog
	fatal: your current branch 'main' does not have any commits yet

	@Liangliang-Shang ➜ ~/test (main) $ touch hello2git	           # New file - Untracked to GIT!

	@Liangliang-Shang ➜ ~/test (main) $ git status
	On branch main
	
	No commits yet
	
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)
	        hello2git
	
	nothing added to commit but untracked files present (use "git add" to track)
  ```
* **`Cached`**
  ```bash
	@Liangliang-Shang ➜ ~/test (main) $ git add hello2git 

	@Liangliang-Shang ➜ ~/test (main) $ git status
	On branch main
	
	No commits yet
	
	Changes to be committed:
	  (use "git rm --cached <file>..." to unstage)
	        new file:   hello2git
  ```
* **`Committed`**
  ```bash
	@Liangliang-Shang ➜ ~/test (main) $ git commit -m "New file: hello2git"
	[main (root-commit) dffcb0f] New file: hello2git
	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 hello2git
  
	@Liangliang-Shang -> ~/test (main) $ git status
	On branch main
	nothing to commit, working tree clean
  
	@Liangliang-Shang -> ~/test (main) $ git log
	commit dffcb0fa795b3de3c26612395b6698c55bb50e5f (HEAD -> main)
	Author: Liangliang <liangliang.shang@icloud.com>
	Date:   Sun Feb 25 14:11:55 2024 +0800
           
		New file: hello2git
  
	@Liangliang-Shang -> ~/test (main) $ git reflog
	dffcb0f (HEAD -> main) HEAD@{0}: commit (initial): New file: hello2git
  ```
* **`Tracked`**
	+ **`Unstaged`**
	  ```
		@Liangliang-Shang ➜ ~/test (main) $ echo "Hello to GIT!" >> hello2git	# Modify a tracked file
		
		@Liangliang-Shang ➜ ~/test (main) $ git status
		On branch main
		Changes not staged for commit:
		  (use "git add <file>..." to update what will be committed)
		  (use "git restore <file>..." to discard changes in working directory)
		        modified:   hello2git
		
		no changes added to commit (use "git add" and/or "git commit -a")
		
		# `git diff` would show changes in the working tree not yet staged for the next commit
		@Liangliang-Shang ➜ ~/test (main) $ git diff
		diff --git a/hello2git b/hello2git
		index e69de29..0a3b6d2 100644
		--- a/hello2git
		+++ b/hello2git
		@@ -0,0 +1 @@
		+Hello to GIT!
	  ```
	+ **`Staged`**
	  ```
		@Liangliang-Shang ➜ ~/test (main) $ git add hello2git 

		@Liangliang-Shang ➜ ~/test (main) $ git status
		On branch main
		Changes to be committed:
		  (use "git restore --staged <file>..." to unstage)
		        modified:   hello2git

		@Liangliang-Shang ➜ ~/test (main) $ git diff				# no diff? as `git add` already run!

		@Liangliang-Shang ➜ ~/test (main) $ git diff --staged		# diff between staged and last commit!
		diff --git a/hello2git b/hello2git
		index e69de29..0a3b6d2 100644
		--- a/hello2git
		+++ b/hello2git
		@@ -0,0 +1 @@
		+Hello to GIT!

		@Liangliang-Shang ➜ ~/test (main) $ git diff --cached		# diff between cached and last commit!
		diff --git a/hello2git b/hello2git
		index e69de29..0a3b6d2 100644
		--- a/hello2git
		+++ b/hello2git
		@@ -0,0 +1 @@
		+Hello to GIT!
	  ```
	+ **`Committed`**
	  ```
		@Liangliang-Shang ➜ ~/test (main) $ git commit -m "Add line: Hello to GIT!"
		[main 093d0e2] Add line: Hello to GIT!
		 1 file changed, 1 insertion(+)

		@Liangliang-Shang ➜ ~/test (main) $ git status
		On branch main
		nothing to commit, working tree clean

		@Liangliang-Shang ➜ ~/test (main) $ git log
		commit 093d0e265ab4ad8e82ed17eab5bca6c85dca08d4 (HEAD -> main)
		Author: Liangliang <liangliang.shang@icloud.com>
		Date:   Sat Feb 24 06:35:06 2024 +0000
		
		    Add line: Hello to GIT!
		
		commit 0451cd32e64bfbfdd3ab4a7e26d99153ff08170b
		Author: Liangliang <liangliang.shang@icloud.com>
		Date:   Sat Feb 24 06:12:48 2024 +0000
		
		    Initial Commit: hello2git

		@Liangliang-Shang ➜ ~/test (main) $ git reflog
		093d0e2 (HEAD -> main) HEAD@{0}: commit: Add line: Hello to GIT!
		0451cd3 HEAD@{1}: commit (initial): Initial Commit: hello2git
	  ```
