abhinavprateek@BNXL-83364-WL:~$ cd assign/
abhinavprateek@BNXL-83364-WL:~/assign$ git status
On branch origin
nothing to commit, working tree clean
abhinavprateek@BNXL-83364-WL:~/assign$ rm -r assign
rm: cannot remove 'assign': No such file or directory
abhinavprateek@BNXL-83364-WL:~/assign$ cd ..
abhinavprateek@BNXL-83364-WL:~$ rm -r assign
rm: remove write-protected regular file 'assign/.git/objects/a0/0342ebccb3b0a7f3e52a9cbce0d7efd025f0c6'? y
rm: remove write-protected regular file 'assign/.git/objects/94/34679323d83ad946b64f9b11243d92e83c58d3'? y
rm: remove write-protected regular file 'assign/.git/objects/a1/44c9afa41531481b88c42b4b64e749cce13cb4'? y
abhinavprateek@BNXL-83364-WL:~$ mkdir assign
abhinavprateek@BNXL-83364-WL:~$ cd assign/
abhinavprateek@BNXL-83364-WL:~/assign$ vi abc.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: will change to "main" in Git 3.0. To configure the initial branch name
hint: to use in all of your new repositories, which will suppress this warning,
hint: call:
hint:
hint:   git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint:   git branch -m <name>
hint:
hint: Disable this message with "git config set advice.defaultBranchName false"
Initialized empty Git repository in /home/abhinavprateek/assign/.git/
abhinavprateek@BNXL-83364-WL:~/assign$ git add .
abhinavprateek@BNXL-83364-WL:~/assign$ git commit -m "Initial commit"
[master (root-commit) 5fe1532] Initial commit
1 file changed, 2 insertions(+)
create mode 100644 abc.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git branch -M main
abhinavprateek@BNXL-83364-WL:~/assign$ git push -u origin main
fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
abhinavprateek@BNXL-83364-WL:~/assign$ git switch -c rebase-demo
Switched to a new branch 'rebase-demo'
abhinavprateek@BNXL-83364-WL:~/assign$ ^C
abhinavprateek@BNXL-83364-WL:~/assign$ vi notes.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git add .
abhinavprateek@BNXL-83364-WL:~/assign$ git commit -m "Rebase-trial"
[rebase-demo f001c02] Rebase-trial
1 file changed, 3 insertions(+)
create mode 100644 notes.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git switch main
Switched to branch 'main'
abhinavprateek@BNXL-83364-WL:~/assign$ vi ab.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git add .
abhinavprateek@BNXL-83364-WL:~/assign$ git commit -m "Update main"
[main 4ff17f5] Update main
1 file changed, 2 insertions(+)
create mode 100644 ab.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git switch rebase-demo
Switched to branch 'rebase-demo'
abhinavprateek@BNXL-83364-WL:~/assign$ git rebase main
Successfully rebased and updated refs/heads/rebase-demo.
abhinavprateek@BNXL-83364-WL:~/assign$ git log --oneline --decorate --graph --all
2a04904 (HEAD -> rebase-demo) Rebase-trial
4ff17f5 (main) Update main
5fe1532 Initial commit
abhinavprateek@BNXL-83364-WL:~/assign$ git switch -c cherrypick-demo
Switched to a new branch 'cherrypick-demo'
abhinavprateek@BNXL-83364-WL:~/assign$ git cherrypick 4ff17f5
git: 'cherrypick' is not a git command. See 'git --help'.
The most similar command is
cherry-pick
abhinavprateek@BNXL-83364-WL:~/assign$ git cherry-pick 4ff17f5
On branch cherrypick-demo
You are currently cherry-picking commit 4ff17f5.
(all conflicts fixed: run "git cherry-pick --continue")
(use "git cherry-pick --skip" to skip this patch)
(use "git cherry-pick --abort" to cancel the cherry-pick operation)
nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:
    git commit --allow-empty

Otherwise, please use 'git cherry-pick --skip'
abhinavprateek@BNXL-83364-WL:~/assign$ git log --oneline -5
2a04904 (HEAD -> cherrypick-demo, rebase-demo) Rebase-trial
4ff17f5 (main) Update main
5fe1532 Initial commit
abhinavprateek@BNXL-83364-WL:~/assign$ git switch main
fatal: cannot switch branch while cherry-picking
Consider "git cherry-pick --quit" or "git worktree add".
abhinavprateek@BNXL-83364-WL:~/assign$ git cherry-pick --quit
abhinavprateek@BNXL-83364-WL:~/assign$ git switch main
Switched to branch 'main'
abhinavprateek@BNXL-83364-WL:~/assign$ vi ab.txt
abhinavprateek@BNXL-83364-WL:~/assign$ vi report.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git add .
abhinavprateek@BNXL-83364-WL:~/assign$ git commit -m "Cherrypick report"
[main 61d9f08] Cherrypick report
1 file changed, 1 insertion(+)
create mode 100644 report.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git log --oneline
61d9f08 (HEAD -> main) Cherrypick report
4ff17f5 Update main
5fe1532 Initial commit
abhinavprateek@BNXL-83364-WL:~/assign$ git switch cherry-pick-practice
fatal: invalid reference: cherry-pick-practice
abhinavprateek@BNXL-83364-WL:~/assign$ git switch cherrypick-demo
Switched to branch 'cherrypick-demo'
abhinavprateek@BNXL-83364-WL:~/assign$ git cherry-pick 61d9f08
[cherrypick-demo 1646c7f] Cherrypick report
Date: Tue Nov 3 11:33:24 2026 +0000
1 file changed, 1 insertion(+)
create mode 100644 report.txt
abhinavprateek@BNXL-83364-WL:~/assign$ git logs
git: 'logs' is not a git command. See 'git --help'.
The most similar command is
log
abhinavprateek@BNXL-83364-WL:~/assign$ git log
commit 1646c7fa956aef451aa59a4a32c055fc00118bb2 (HEAD -> cherrypick-demo)
Author: abhinav-prateek-xor Abhinav.Prateek@xoriant.com
Date:   Tue Nov 3 11:33:24 2026 +0000
    Cherrypick report

commit 2a0490496ca96e88d3526aa568badd3db9425b6f (rebase-demo)
Author: abhinav-prateek-xor Abhinav.Prateek@xoriant.com
Date:   Tue Nov 3 11:27:07 2026 +0000
    Rebase-trial

commit 4ff17f5cb7f08914a444c05c74c5537b3c5a85e3
Author: abhinav-prateek-xor Abhinav.Prateek@xoriant.com
Date:   Tue Nov 3 11:28:53 2026 +0000
    Update main

commit 5fe1532a7487e4c3f6c30baa4a1a9655c3f82955
Author: abhinav-prateek-xor Abhinav.Prateek@xoriant.com
Date:   Tue Nov 3 11:23:39 2026 +0000
    Initial commit
abhinavprateek@BNXL-83364-WL:~/assign$ git log --oneline
1646c7f (HEAD -> cherrypick-demo) Cherrypick report
2a04904 (rebase-demo) Rebase-trial
4ff17f5 Update main
5fe1532 Initial commit
abhinavprateek@BNXL-83364-WL:~/assign$
