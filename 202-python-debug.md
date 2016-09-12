# Python Debugging


* pdb
* ipdb
* pudb
* google-python-cloud-debugger

## pdb - The Python Debugger

https://docs.python.org/3/library/pdb.html

The module `pdb` defines an interactive source code debugger for Python programs. It supports setting(conditional) breakpoints and single steppinig at the source line level, inspection of stack frames, source code listing, and evaluation of arbitrary Python code in the context of any stack frame. It also supports post-mortem debugging and can be called under program control.

The debugger is extensible -- it is actually defined as the class Pdb. This is currently undocumented but easily understood by reading the source. The extension interface uses the modules bdb and cmd.

The debugger's prompt is `(Pdb)`. Typical usage to run a program under control of the debugger is:

```
>>> import pdb
>>> import mymodule
>>> pdb.run('mymodule.test()')
> <string>(0)?()
(Pdb) continue
> <string>(1)?()
(Pdb) continue
NameError: 'spam'
> <string>(1)?()
(Pdb)
```

_Changed in verion 3.3_: Tab-completion via the readline module is available for commands and command arguments, e.g. the current global and local names are offered as arguments of the p command.

pdb.py can also be invoked as a script to debug other scripts. For example:

    python3 -m pdb myscript.py

When invoked as a script, pdb will automatically enter post-mortem debugging if the program being debugged exits abnormally. After post-mortem debugging(or after normal exit of the program), pdb will restart the program. Automatic restarting preserves pdb's state(such as breakpoints) and in most cases is more useful than quitting the debugger upon program's exit.

_New in version 3.2_: `pdb.py` now accepts a `-c` option that executes commands as if given in a .pdbrc file.

The typical usage to break into the debugger from a running program is to insert

    import pdb; pdb.set_trace()

at the location you want to break into the debugger. You can then step through the code following this statement, and continue running without the debugger using the `continue` command.

The typical usage to inspect a crashed program is:

```
>>> import pdb
>>> import mymodule
>>> mymodule.test()
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "./mymodule.py", line 4, in test
    test2()
  File "./mymodule.py", line 3, in test2
    print(spam)
NameError: spam
>>> pdb.pm()
> ./mymodule.py(3)test2()
-> print(spam)
(Pdb)
```

__Debugger Commands__

The commands recognized by the debugger are listed below. Most commands can be abbreviated to one or two letters as indicated; e.g. `h(elp)` means that either `h` or `help` can be used to enter the help command(but not `he` or `hel`, nor `H` or `Help` or `HELP`). Arguments to commands must be separated by whitespace(spaces or tabs). Optional arguments are enclosed in square brackets (`[]`) in the command syntax; the square brackets must not be typed. Alternatives in the command syntax are separated by a vertical bar (`|`)

Entering a blanking line repeats the last command entered. Exception: if the last command was a `list` command, the next 11 lines are listed.

Commands that the debugger doesn't recognize are assumed to be Python statements and are executed in the context of the program being debugged. Python statements can also be prefixed with an exclamation point(`!`). This is a powerful way to inspect the program being debugged; it is even possible to change a variable or call a function. When an exception occurs in such a statement, the exception name is printed but the debugger's state is not changed.

The debugger supports aliases. Aliases can have parameters which allows one a certain level of adapability to the context under examination.

Multiple commands may be extered on a single line, separated by `;;`(A single `;` is not used as it is the separator for multiple commands in a line that is passed to the Python parser.) No intelligence is applied to separating the commands; the input is split at the first `;;` pair, enev if it is the middle of a quoted string.

If a file `.pdbrc` exists in the user's home directory or in the current directory, it is read in and executed as if it had been typed at the debugger prompt. The is particularly useful for aliases. If both file exist, the one in the home directory is read first and aliases defined there can be overridden by the local file.

_Changed in version 3.2_: `.pdbrc` can now contain commands that continue debugging, such as `continue` or `next`. Previouly, these commands had no effect.

```
h(elp) [command]
w(here)
d(own) [count]
u(p) [count]
b(reak) [([filename:]lineno | function) [, condition]]
tbreak [([filename:]lineno | function) [, condition]]
cl(ear) [filename:lineno | bpnumber [bpnumber ...]]
disable [bpnumber [bpnumber ...]]
enable [bpnumber [bpnumber ...]]
ignore bpnumber [count]
conditioin bpnumber [condition]
commands [bpnumber]
s(tep)
n(ext)
unt(il) [lineno]
r(eturn)
c(ont(inue))
j(ump) lineno
l(ist) [first[, last]]
ll | longlist
a(rgs)
p expression
pp expression
whatis expression
source expressioin
display [expression]
undisplay [expression]
interact
alias [name [command]]
unalias name
! statement
run [args ...]
restart [args ...]
q(uit)
```
