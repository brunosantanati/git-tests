# GIT Tests

Repo to test some GIT features.  

## Useful Links

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

## Useful Commands
```
Squash commits:
git rebase -i HEAD~2
The command above will show the last 2 commits, so supposing you want to join them into only one commit, you can mark the second one with the flag squash in front of it, exit and save. If these 2 commits that became 1 were already in GitHub, you need to use the -f flag (force) to overwrite the remote repo history as below (don't do this if any other person has pulled the code before).
git push -f origin main

See differences staged:
git diff --staged

Commit some modifications in the file and not others:
git add -p
```
