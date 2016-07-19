# SSH

## git push problem

PROBLEM:

[michael@localhost misc]$ git push
Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

SOLVTION:

change url in .git/config from
    url = ssh://github.com/darth001/misc.git
to
    url = ssh://git@github.com/darth001/misc.git # standard ssh protocol, RECOMMENDED
or
    url = git@github.com:darth001/misc.git       # alternative ssh protocol with scp-like syntax

CAUSE:

Everything is OK some days ago.
And when command below executed, expected results can also be got:
    $ ssh -vT git@github.com


