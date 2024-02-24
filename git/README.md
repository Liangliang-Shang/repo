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
