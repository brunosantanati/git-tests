# GIT Tests

Repo to test some GIT features.  

## Useful Links

GH Links:  
[Take GitHub to the command line](https://cli.github.com/)  
[Installing gh on Linux and BSD](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)  

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

Videos regarding rebase, squash and other commands:  
[Usando Git Direito | Limpando seus Commits!](https://youtu.be/6OokP-NE49k)  
[How to squash and rebase in git](https://youtu.be/AWayLpQHJeE)  
[Modifying git History (3/3) - Pulling a shared branch with rebase to catch up](https://youtu.be/-H2U3kJ_urw)  
[How to edit Git history - fix any mistake](https://www.youtube.com/live/lYZeaQWjqSk?feature=share)  
[git rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)  
[Rewriting History](https://www.atlassian.com/git/tutorials/rewriting-history)  

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

Squash commits:
git rebase -i HEAD~2
The command above will show the last 2 commits, so supposing you want to join them into only one commit, you can mark the second one with the flag squash in front of it, exit and save. If these 2 commits that became 1 were already in GitHub, you need to use the -f flag (force) to overwrite the remote repo history as below (don't do this if any other person has pulled the code before).
git push -f origin main

##################################################

See differences staged:
git diff --staged

##################################################

Commit some modifications in the file and not others:
git add -p

##################################################

Display a graphical view of the commit history considering all branches:
git log --oneline --graph --all

##################################################

Add untracked file using interactive mode:
git add -i
Select the option '4: add untracked'
Type the numbers of the files you want to add
When finished type enter
Type 7 to exit (option '7: quit')

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
```
