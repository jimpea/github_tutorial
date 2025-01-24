# Git and GitHub

- Git and GitHub are not the same thing.
- Git is a version control system - you install and use this on your local workstation.
- Git allows you to create separate repositories -- 'repos' -- for each project or document set
- GitHub is a web service that hosts your repos. If you make your work public, then anyone can view and download your repo.
- Astrea has a private GitHub account so that we can use this to host and distribute the repos within Astrea.
- Host your public repos on GitHub for free, for instance mine is here: <https://github.com/jimpea>.

## Install Git

Download and run the installer from <https://git-scm.com/downloads/win>

## Use Git

Many IDEs offer git integration, for instance RStudio and VScode, learn how to use this from the help offered in these environments. However, I think that you should start off using this from a command line (terminal).

### Create a Repository

Make a folder for your new repository, for instance on my desktop, I will make a new folder in my `play` area -- I use this for experiments (playing around):

```bash
(py11) PS W:\play> mkdir git_tutorial
```

Move to this folder and make it into a git repo:

```bash
(py11) PS W:\play> cd .\git_tutorial\
(py11) PS W:\play\git_tutorial> git init
Initialized empty Git repository in //cam-svr01/promdata/jpearson/play/git_tutorial/.git/
```
Make a new file, or copy one of your existing documents here -- I will use this document! List the contents of the folder to confirm:

```bash
(py11) PS W:\play\git_tutorial> cp C:\Users\jpearson\Downloads\git_intro.md .
(py11) PS W:\play\git_tutorial> ls


    Directory: W:\play\git_tutorial


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        17/01/2025     16:26            876 git_intro.md
```

Have a look at your git staging area, this is where git gathers all files that have changed:

```bash
(py11) PS W:\play\git_tutorial> git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        git_intro.md

nothing added to commit but untracked files present (use "git add" to track)
```

This shows that the file `git-intro.md` has changed, but has not been committed yet. Add this to the files that will be committed to the repo. *Note that git is set up to work with files made on linux systems which end all text lines with two characters: cursor return and line feed (think about how an old typewriter works). Windows only uses a single line feed character to mark the end of a line. You can safely ignore this*

```bash
(py11) PS W:\play\git_tutorial> git add --all
warning: in the working copy of 'git_intro.md', LF will be replaced by CRLF the next time Git touches it
```

The file has now moved to the staging area:

```

(py11) PS W:\play\git_tutorial> git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   git_intro.md
```

Add the changes to the git repo, along with a message, then look at the git log to see the file history: the commit message is very important here, so you should take care to ensure that this communicates the purpose of the update:

```bash
(py11) PS W:\play\git_tutorial> git commit --all -m "Make initial file version"
[master (root-commit) e518385] Make initial file version
 1 file changed, 18 insertions(+)
 create mode 100644 git_intro.md
(py11) PS W:\play\git_tutorial> git log
commit e518385f4cb851661e26010dde458ee3c9123b34 (HEAD -> master)
Author: Jpearson <j.pearson@gmail.com>
Date:   Fri Jan 17 16:45:44 2025 +0000

    Make initial file version
```

This new line will update this file once I save it, look  at the git status to show the modified files:

 ```bash
 (py11) PS W:\play\git_tutorial> git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   git_intro.md

no changes added to commit (use "git add" and/or "git commit -a")
 ```
 
As before, add the file to the staging and commit with a new commit message. The log now contains two entries:

```bash
(py11) PS W:\play\git_tutorial> git log
commit 88da01221e911ba99c6f180fee83f78920a42ad4 (HEAD -> master)
Author: Jpearson <j.pearson@gmail.com>
Date:   Fri Jan 17 16:54:10 2025 +0000

    Add a new commit pointing to see how the git log works

commit e518385f4cb851661e26010dde458ee3c9123b34
Author: Jpearson <j.pearson@gmail.com>
Date:   Fri Jan 17 16:45:44 2025 +0000

    Make initial file version
```

The git log provides a history of your file. You can revert all your changed to an earlier commit. In this way you retain control over the files.

Your repo can contain many files and sub folders.

## Sharing Your Repo

This is where GitHub comes in:

Upload your new repository to your github account, make it public you can then share it with anyone. Follow the github instructions [here](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).

I have added a new empty repo to github, now link this local repo with the new github repo

```bash
(py11) PS W:\play\git_tutorial> git remote add origin https://github.com/jimpea/github_tutorial.git
(py11) PS W:\play\git_tutorial> git branch -M main
(py11) PS W:\play\git_tutorial> git push -u origin main
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 2.87 KiB | 81.00 KiB/s, done.
Total 9 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/jimpea/github_tutorial.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

You can now look at this file here: <https://github.com/jimpea/github_tutorial>. You can continue to make changes locally and update Github:

First commit all the changes that push to github:

```bash
(py11) PS W:\play\git_tutorial> git commit --all -m "Push the latest commit to github"
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
(py11) PS W:\play\git_tutorial> git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 675 bytes | 56.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/jimpea/github_tutorial.git
   aea0e26..518b220  main -> main
```

## Using Revert asd Reset

Each entry into the git log carries a unique reference number. This is used when you want to go back to an earlier version of the repository. So, I shall add the current version of this file to the repo and then list the last three commits:

```bash
W:\play\git_tutorial> git commit --all -m "Add section for Revert and Reset"
...
(base) PS W:\play\git_tutorial> git log --oneline -n 3
c2b8db4 (HEAD -> main) Add section for Revert and Reset
7c8f9b4 (origin/main) Revert "Remove explicit paths"
56845e6 Add temporart line
```

Now revert to the previous commit 'Revert "Remove explicit paths"': this has the number c2b8db4. 

```bash
(base) PS W:\play\git_tutorial> git reset 7c8f9b4
(base) PS W:\play\git_tutorial> git log --oneline -n 3
7c8f9b4 (HEAD -> main, origin/main) Revert "Remove explicit paths"
56845e6 Add temporart line
d9339f2 Remove explicit paths
```

This retains the current state of the file, but moves the commit history back. This allows you to amend the current changes and commit again. If you want to remove all the changes to the file, add the `--hard` flag to the line like this: `git reset 7c8f9b4 --hard`.

`get reset` performs the same task, but registers a new log entry. This ensures that the git commit history maintains coordination with the github archive.

For more information see [here](https://www.freecodecamp.org/news/git-reverting-to-previous-commit-how-to-revert-to-last-commit/). This provides the following summary:

> ## When to Use git reset and git revert
>
> You should use git reset when working on a local repository with changes yet to be pushed remotely. This is because running this command after pulling changes from the remote repo will alter the commit history of the project, leading to merge conflicts for everyone working on the project.
>
> `git reset` is a good option when you realize that the changes being made to a particular local branch should be somewhere else. You can reset and move to the desired branch without losing your file changes.
>
> `git revert` is a good option for reverting changes pushed to a remote repository. Since this command creates a new commit, you can safely get rid of your mistakes without rearranging the commit history for everyone else.
