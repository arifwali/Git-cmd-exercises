# cmd-example
Git cmd assigment
# Configuring Git

Input:

PS C:\Users\Username\Desktop\cmd-example> git config --global user.name "Arif wali"
PS C:\Users\Username\Desktop\cmd-example>  git config --global user.email "arif.zamanwali@hotmail.com"
PS C:\Users\Username\Desktop\cmd-example>  git config --global color.ui true
PS C:\Users\Username\Desktop\cmd-example>  git config --list

output:

color.diff=auto
color.status=auto
color.branch=auto
color.interactive=true
user.email=arif.zamanwali@hotmail.com
user.name=Arif wali

# Starting a New Local Repository with Git

PS C:\Users\Username\Desktop\cmd-example> git init
initialized existing Git repository in C:/Users/Username/Desktop/cmd-example/.git/
PS C:\Users\Username\Desktop\cmd-example> git status
On branch master
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean

# Add Files with Git

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ touch new-test.txt
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ ls
git-cheat-sheet-large01.png  new-test.txt  README.md

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git add new-test.txt

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git status
On branch master
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   new-test.txt
# add multiple or all files
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git add another-file.txt assignment-file.md
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ ls
another-file.txt  assignment-file.md  git-cheat-sheet-large01.png  new-test.txt  README.md

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git status
On branch master
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   another-file.txt
        new file:   assignment-file.md
        new file:   new-test.txt

What if the project grows enormously and you have to add more than three files? How can we add a dozen files (or dozens of files) in one go?the following solution:

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git add .

"git add ." command will only add files located in the root directory. But the root directory may contain many other directories with files. How can we add files from those other directories plus the files in the root directory to the staging area? command below:
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git add --all
# removing files from the staging area.
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git rm --cached new-test.txt
rm 'new-test.txt'

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git status
On branch master
Your branch is behind 'origin/master' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   another-file.txt
        new file:   assignment-file.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        new-test.txt

# "reset" command:
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git reset another-file.txt

# Committing Changes to Git

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git commit -m "Add files"
[master 20610fd] Add files
 1 file changed, 294 insertions(+)
 create mode 100644 assignment-file.md
 
 add modified files to the staging area and commit them at the same time.
 $ git commit -a -m "Do something once more"

There will be times when you'll regret committing to a repository. Let's say you've modified ten files, but committed only nine. How can you add that remaining file to the last commit? And how can you modify a file if you've already committed it? There are two ways out. First, you can undo the commit:

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git reset --soft HEAD^

Instead of resetting the HEAD and undoing the last commit, we can rectify a commit by using the "--amend" option when committing to a repository. Just add the remaining file to the staging area and then commit:

$ git add file-i-forgot-to-add.html
$ git commit --amend -m "Add the remaining file"

# Push and Pull To and From a Remote Repository

Now you need to bind this remote repository to your local repository:

$ git remote add origin https://github.com/YourUsername/some-small-app.git

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git push origin master
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 5.81 KiB | 2.90 MiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/arifwali/cmd-example.git
   27627f0..b592421  master -> master

Now that you've added a remote repository, you can view the list of repositories by running the following command:

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$  git remote -v
origin  https://github.com/arifwali/cmd-example.git (fetch)
origin  https://github.com/arifwali/cmd-example.git (push)

"clone" command:

$ git clone git@github.com:YourUsername/your-app.git

# pull
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git pull
Updating fd0b4c3..27627f0
Fast-forward
 .idea/cmd-example.iml | 12 ++++++++++++
 .idea/misc.xml        |  4 ++++
 .idea/modules.xml     |  8 ++++++++
 .idea/vcs.xml         |  6 ++++++
 Newfile               |  1 +
 5 files changed, 31 insertions(+)
 create mode 100644 .idea/cmd-example.iml
 create mode 100644 .idea/misc.xml
 create mode 100644 .idea/modules.xml
 create mode 100644 .idea/vcs.xml
 create mode 100644 Newfile

# Branches

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git branch
* master
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git branch test1
* master
  test1
  
  Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git branch test2
* master
  test1
  test2
  
  Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git checkout test1
Switched to branch 'test1'
Your branch is up to date with 'origin/test1'.

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (test1)
$ git branch
  master
* test1
  test2

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (test1)
$ git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

merge the user-profile branch using the command "merge":
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git merge test1
Already up to date.

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git merge test2
Already up to date.

Delete
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git branch -d test3
Deleted branch test3 (was b592421).

But instead of running two commands you can run only one:

$ git checkout -b admin-panel

# fetch
Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git fetch origin

# Tagging

# log

Username@DESKTOP-IM5TB77 MINGW64 ~/Desktop/cmd-example (master)
$ git log
commit b59242154acbccbaf626d9386fa2e9a0ac7e6aa2 (HEAD -> master, tag: 0.1.0, origin/master, origin/HEAD)
Author: Arif wali <arif.zamanwali@hotmail.com>
Date:   Tue Jun 11 11:07:28 2019 +0300

    new files

commit 27627f00411712ecd8ef033a4d9ab8e74378239b
Author: arifwali <47124591+arifwali@users.noreply.github.com>
Date:   Mon Jun 10 16:05:01 2019 +0300

    Create Newfile

commit 6d699e42498fb2f1a17285060811f035620437eb
Author: arif wali <arif.zamanwali@hotmail.com>
Date:   Mon Jun 10 15:50:28 2019 +0300

    pycham

commit fd0b4c3ac612861aa6c87d16ec175b151747ed82
Author: arif wali <arif.zamanwali@hotmail.com>
Date:   Mon Jun 10 14:53:22 2019 +0300

    test remove

commit 319d57399587b825ac5586b27650734dabc385c9
Author: arif wali <arif.zamanwali@hotmail.com>
Date:   Mon Jun 10 12:16:52 2019 +0300

    removed

commit 75c9b5f070b2c77d58584e18d23431f83542a8d7
Author: arifwali <arif.zamanwali@hotmail.com>
Date:   Mon Jun 10 11:38:30 2019 +0300

    Create notes.txt

commit fbdc4337d8911da1d3d4b1c00f841e1127a474e8
Author: arifwali <arif.zamanwali@hotmail.com>
Date:   Mon Jun 10 11:35:29 2019 +0300

    Create .gitignore.txt

commit 6fc9939b45fbcdf3570b25a58af51793a69e6174 (origin/test2, origin/test1, test2, test1)
Author: arifwali <47124591+arifwali@users.noreply.github.com>
Date:   Mon Jun 10 10:10:39 2019 +0300

    Initial commit





