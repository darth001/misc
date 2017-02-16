#

## Rename remote branches

You just have to create a new local branch with the desired name, push it to remote, and then delete the old remote branch:

    $ git branch new-branch-name origin/old-branch-name
    $ git push origin --set-upstream new-branch-name
    $ git push origin :old-branch-name

Then, to see the old branch name, each client of the repository would have to:

    $ git fetch origin
    $ git remote prune origin

NOTE: If old branch is main branch, you should change the main branch settings. Otherwise, when you run `git push origin :old-branch-name`, you'll get error of "deletion of the current branch prohibited".

## Create an empty branch

    $ git checkout --orphan new-branch-name
    $ git rm --cached -r .
    $ ...
    $ git push origin new-branch-name
