# GIT Tests

Repo to test some GIT features.  

## Useful Links

GH Links:  
[Take GitHub to the command line](https://cli.github.com/)  
[Installing gh on Linux and BSD](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)  
[Recovering Deleted Files in GitHub](https://rewind.com/blog/recovering-deleted-files-in-github/)  

GIT Workflows  
[Comparing Git Workflows: What You Should Know](https://www.atlassian.com/git/tutorials/comparing-workflows)  
[Git Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)  
[Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)  
[Forking Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow)  
[5 Different Git Workflows](https://medium.com/javarevisited/5-different-git-workflows-50f75d8783a7)  
[4 branching workflows for Git](https://medium.com/@patrickporto/4-branching-workflows-for-git-30d0aaee7bf)  

GIT Bisect:  
[Using Git Bisect](https://youtu.be/P3ZR_s3NFvM)  
[Git Bisect | How to use Git Bisect | Learn Git](https://youtu.be/z-AkSXDqodc)  
[Git bisect tutorial. How to find a bad bug commit.](https://youtu.be/D7JJnLFOn4A)  

GIT Rebase:  
[When to use ‘Git Rebase’ explained](https://medium.com/@harishlyadav/when-to-use-git-rebase-explained-3c8192cba5c7)  
[when not to use "git rebase" while working with GIT branches?](https://stackoverflow.com/questions/31406079/when-not-to-use-git-rebase-while-working-with-git-branches)  
[Rebasing and what does one mean by rebasing pushed commits](https://stackoverflow.com/questions/2715085/rebasing-and-what-does-one-mean-by-rebasing-pushed-commits)  
[git merge vs git rebase: Avoiding Rebase Hell](https://jarrodspillers.com/blog/git/2009-08-19-git-merge-vs-git-rebase-avoiding-rebase-hell/)  
[Rebase Considered Harmful](https://changelog.complete.org/archives/586-rebase-considered-harmful)  
[The Ultimate Guide to Git Merge and Git Rebase](https://www.google.com/amp/s/www.freecodecamp.org/news/the-ultimate-guide-to-git-merge-and-git-rebase/amp/)  
[How to Use git rebase -i to Combine First Two Commits in a Git Repository](https://gunnariauvinen.com/posts/how-to-use-git-rebase-i-to-combine-first-two-commits-in-a-git-repository/)  

Links regarding rebase and squash:  
[How to squash and rebase in git](https://youtu.be/AWayLpQHJeE)  
[Modifying git History (3/3) - Pulling a shared branch with rebase to catch up](https://youtu.be/-H2U3kJ_urw)  
[How to edit Git history - fix any mistake](https://www.youtube.com/live/lYZeaQWjqSk?feature=share)  
[git rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)  
[Rewriting History](https://www.atlassian.com/git/tutorials/rewriting-history)  

Links regargind cherry-pick:  
[How To Cherry Pick Git Commits | When & How to use a Git Cherry Pick Commit?](https://www.junosnotes.com/git/how-to-cherry-pick-git-commits/)  

Links for various different GIT commands:  
[Usando Git Direito | Limpando seus Commits!](https://youtu.be/6OokP-NE49k)  

## GitHub Command Line (gh) Installation in Ubuntu
```
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

## gh Commands
```
Authenticate on gh:
gh auth login

Get help:
gh --help
gh repo --help
gh repo create --help

Create a new repo in GitHub:
gh repo create git-tests --description "Repo to test some GIT features" --public --clone --add-readme
```

## Useful Commands
```
Rebase:
The example below might be used when the main branch is ahead of your feature branch, so basically you've based your branch on an older commit that is not the HEAD of the main anymore. You are in your own feature branch and you want to make the HEAD of the main the base for the code and re-apply your changes on top of it. We're assuming that there are new commits both in main and in your branch.
git checkout my-branch
git rebase main
if you're finished you can merge all your work back to main:
git checkout main
git merge my-branch

##################################################

Delete last commit but preserve the related changes in the staging area:
git reset --soft HEAD~1

Delete last commit but preserve the related changes in the working directory (unstaged):
git reset HEAD^

Delete last commit but it DOES NOT preserve the related changes (CAUTION: it's not reversable):
git reset --hard HEAD~1

##################################################

Squash commits:
git rebase -i HEAD~2
The command above will show the last 2 commits, so supposing you want to join them into only one commit, you can mark the second one with the flag squash in front of it, exit and save. If these 2 commits that became 1 were already in GitHub, you need to use the -f flag (force) to overwrite the remote repo history as below (don't do this if any other person has pulled the code before).
git push -f origin main

Squash the two only commits you have:
git rebase -i --root

##################################################

Modify changes made in one specific commit
OR
Move changes from one commit to another:

https://stackoverflow.com/questions/15213814/how-should-i-move-changes-from-one-commit-to-another

1 - git rebase -i HEAD~2
2 - Put the 'edit' word in front of the commit you want to change:
edit 97e9d62 Commit C, editing file2.txt
3 - Edit the file you want to.
4 - git add .
5 - git commit --amend
6 - git rebase --continue

##################################################

Change commit message for a specific commit:
git rebase -i HEAD~2
Run the command above, but make sure to replace the number 2 for the appropriate number to list all past commits including the one you want to change.
You should type 'reword' in front the commit you want to change its message and exit/save. The editor will open so you can change the commit message.

##################################################

Unstage a file:
git reset -- <file>
OR
git restore --staged <file>

Unstage all files:
git reset --

##################################################

See differences staged:
git diff --staged

##################################################

Get rid of all local/uncommited changes:
git reset --hard

##################################################

Commit some modifications in the file and not others:
git add -p
After run the command, if we've changed multiple lines of a file we'll be asked:
(1/1) Stage this hunk [y,n,q,a,d,s,e,?]?
We can respond s to split the staging of the changes and choose them separately afterwards.
Type y to stage the change or n to not stage it.

##################################################

Display a graphical view of the commit history considering all branches:
git log --oneline --graph --all

##################################################

Add untracked file using interactive mode:
git add -i
Select the option '4: add untracked'
Type the numbers of the files you want to add to stage
When finished press enter
Select the option '3: revert'
Type the numbers of the files you want to remove from stage
When finished press enter
Type 7 or q to exit (option '7: quit')

##################################################

Find a bad commit, see its content and revert it:
$ git bisect start
$ git bisect bad
$ git bisect good 287d4f
Bisecting: 2 revisions left to test after this (roughly 1 step)
[cd2bb5346a4d974d2b6ce08156dc0bca925fb09d] Change color of animation
$ git bisect good
Bisecting: 0 revisions left to test after this (roughly 1 step)
[fd36f59c5c664e82c150317e107773d0ac7df9dc] Change animation colors
$ git bisect bad
Bisecting: 0 revisions left to test after this (roughly 0 steps)
[9ec1c144d2707b46041f4b921edf7cbba8f06bff] Break animation
$ git bisect bad
9ec1c144d2707b46041f4b921edf7cbba8f06bff is the first bad commit
commit 9ec1c144d2707b46041f4b921edf7cbba8f06bff
Author: Bruno Sant' Ana <bruno.santana.ti@gmail.com>
Date:   Fri Jun 9 03:17:05 2023 -0300

    Break animation

 fake-project/test-bisect/animation.html | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
$ git show 9ec1c14
$ git bisect reset
$ git revert 9ec1c14

##################################################

Change last commit message (rewrite history):
git commit -m "New message here" --amend
OR
git commit --amend

##################################################

Pull changes but using the rebase strategy during the pull operation
git pull --rebase origin main

##################################################

Unset password:
git config --global --unset user.password

##################################################

Get a list of Git branches, ordered by most recent commit:
git for-each-ref --sort=-committerdate refs/heads/
OR
git for-each-ref --sort=-committerdate refs/remotes/
OR
git for-each-ref --sort=-committerdate

##################################################

List all branches created by a specific user/person:

git for-each-ref --format='%(committerdate) %09 %(authorname) %09 %(refname)' --sort=committerdate | grep Bruno

List all branches created by a specific user/person in remote origin:

git for-each-ref --format='%(committerdate) %09 %(authorname) %09 %(refname)' --sort=committerdate | grep Bruno | grep remote
OR
git for-each-ref --format='%(committerdate) %09 %(authorname) %09 %(refname)' --sort=committerdate refs/remotes/origin/ | grep Bruno

If you are seeing branches that has been deleted in remote, use one of these commands to update the list:
git remote prune origin
OR
git fetch origin --prune

##################################################

Solve problem 'Filename too long'
git clone -c core.longpaths=true https://repo.url

##################################################

List all authors that worked on a file (in this case the Dockerfile)
git log --follow -- Dockerfile | grep Author

##################################################

See the graphical tree in terminal:
git log --graph --oneline
or
gitk

##################################################

Change commit message when cherry-picking
git cherry-pick -e <hash>

##################################################

Recover deleted file:

recover the file in the commit f25b431de (when you have the commit SHA that has the exact file version you want)
git checkout f25b431de path/to/the/file/fileName.txt

recover the file in the commit before f25b431de (when you have the commit SHA that deleted the file)
git checkout f25b431de^ path/to/the/file/fileName.txt

##################################################

Check stash entry content:

git stash show -p stash@{0}

##################################################

Filter commits by author:

git log --author="username"
OR
git log --author="SomeName.*" --perl-regexp

##################################################

See overritten commits by rebase:

git reflog show <nome-do-branch>
View details of a specific commit:
git show <commit-hash>

##################################################

Check all commits that changed a specific file:

1. List commits by file:
git log -- <filename>

This command will list all commits that have modified the specified file.

2. Include reflog:
git reflog -- <filename>

This command will list all reflog entries that have modified the specified file. Reflog entries can include commits that have been deleted or reverted.

3. Combine both:
git log -- <filename> --follow

This command will list all commits that have modified the specified file, including commits that have been renamed or moved. It will also follow the file's history through renames and moves.

4. Search for specific changes:
git log --grep="your search term" -- <filename>

This command will list all commits that have modified the specified file and contain the specified search term in the commit message.
```

## How to move a full Git repository  

[How to move a full Git repository](https://www.atlassian.com/git/tutorials/git-move-repository)  

Let’s call the original repository ORI and the new one NEW, here are the steps required to copy everything from ORI to NEW:  

1. Create a local repository in the temp-dir directory using:  

<code>git clone <url to ORI repo> temp-dir</code>  

2. Go into the temp-dir directory.  

3. To see a list of the different branches in ORI do:  

<code>git branch -a</code>  

4. Checkout all the branches that you want to copy from ORI to NEW using:  

<code>git checkout branch-name</code>  

5. Now fetch all the tags from ORI using:  

<code>git fetch --tags</code>  

6. Before doing the next step make sure to check your local tags and branches using the following commands:  

<code>git tag</code>  
<code>git branch -a</code>  

7. Now clear the link to the ORI repository with the following command:  

<code>git remote rm origin</code>  

8. Now link your local repository to your newly created NEW repository using the following command:  

<code>git remote add origin <url to NEW repo></code>  

9. Now push all your branches and tags with these commands:  

<code>git push origin --all</code>  
<code>git push --tags</code>  

10. You now have a full copy from your ORI repo.  

Extra  

If you want to simply copy the entire repository you can use  

<code>git clone --mirror <url to ORI repo> temp-dir</code>  

to replace step 1 to 5.  
