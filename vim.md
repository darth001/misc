#


##

http://www.vim.org/

https://github.com/vim/vim.git


##

[Example vimrc](http://vim.wikia.com/wiki/Example_vimrc)


##

[Indenting source code](http://vim.wikia.com/wiki/Indenting_source_code)

The indent features of Vim are very helpful for indenting source code. This tip discusses settings that affect indentation.

These settings mostly affect the automatic indentation which Vim inserts as you type, but also can be triggered manually with the `=` operator, so that you can easily Fix indentation in your buffer.

__Setup__

_Indentation without hard tabs_

For indentation without tabs, the principle is to set `expandtab`, and set `shiftwidth` and `softtabstop` to the same value, while leaving `tabstop` as tis default value:

```
set expandtab
set shiftwidth=2
set softtabstop=2
```
These settings will result in spaces being used for all indentation.

_Indentation purely with hard tabs_

For indentation with hard tabs, the principle is to set `tabstop` and `shiftwidth` to the same value, and to leave `expandtab` at its default value(`noexpandtab`), and leave `softtabstop` unset:

```
set shiftwidth=2
set softtabstop=2
```
These settings will result in hard tabs being used for all indentation.

_Indentation with mixed tabs and spaces_

For indentation with mixed tabs and spaces, the principle is to set `shiftwidth` and `softtabstop` to the same value, leave `expandtab` as its default(`noexpandtab`). Usually, `tabstop` is left as its default value:

```
set shiftwidth=2
set softtabstop=2
```
These settings will cause as many hard tabs as possible being used for indentation, and spaces will be used to fill in the remains. If you want to distinguish between "indentation" and "alignment", i.e., the number of hard tabs equals the indentation level, use the [Smart Tabs](http://vim.wikia.com/wiki/VimTip1626) plug-in.

_Explanation of the options_

Vim's different indentation options are an endless source of grief and confusion for new users. There are plenty of example vimrcs out there that will tell you how theirs is the proper setup. More often than not, they are misguided. Let `:help` be your reference, and this page be your guide to Vim's indentation options.

`tabstop`
    changes the width of the `TAB` character, plain and simple.

`softtabstop`
    affects what happens when you press the `<TAB>` or `<BS>` keys. Its default value is the same as the value of `tabstop`, but when using indentation without hard tabs or mixed indentation, you want to set it to the same value as `shiftwidth`. If `expandtab` is unset, and `tabstop` is different from `softtabstop`, the `<TAB>` key will minimize the amount of spaces inserted by using multiples of `TAB` characters. For instances, if `tabstop` is 8, and the amount of consecutive space inserted is 20, two `TAB` characters and four spaces will be used.

`shiftwidth`
    affects what happens when you press `>>`, `<<` or `==`. It also affects how automatic indentation works.

`expandtab` affects what happens when you press the `<TAB>` key. If `expandtab` is set, pressing the `<TAB>` key will always insert `softtabstop` amount of space characters. Otherwise, the amount of spaces inserted is minimized by using `TAB` characters.

`smarttab`
    affects how `TAB` key presses are interpreted depending on where the cursor is. If `smarttab` is on, a `<TAB>` keys inserts indentation accouring to `shiftwidth` at the begining of the line, whereas `tabstop` and `softtabstop` are used elsewhere. There is seldom any need to set this option, unless it is necessary to use hard `TAB` characters in body text or code.


##

[How to stop auto indenting](http://vim.wikia.com/wiki/VimTip330)

##

[Toggle auto-indenting for code paste](http://vim.wikia.com/wiki/VimTip906)

Pasting text into a terminal running Vim with automatic indentation enabled can destroy the indentation of the pasted text.

__Background__

If you use Vim commands to paste texts, nothing unexpected occurs. The problem only arises when pasting from another application, and only when you are not using a GUI version of Vim.

In a console or terminal version of Vim, there is no standard procedure to paste text from another application. Instead, the terminal may emulate pasting by inserting text into the keyboard buffer, so Vim thinks the text has been typed by the user. After each line ending, Vim may move the cursor so the next line starts with the same indent as the last. However, that will change the indentation aleady in the pasted text.

__Paste toggle__

:set paste
:set nopaste

or

:set pastetoggle=<F2>

1> Start insert mode
2> Press F2(toggles the 'paste' option on)
3> Use your terminal to paste text from the clipboard
4> Press F2(toggles the 'paste' option off)

__References__
:help paste
:help pastetoggle

##

[Setting the font in the GUI](http://vim.wikia.com/wiki/Setting_the_font_in_the_GUI)

if has('gui_running')
  set guioptions-=T  " no toolbar
  colorscheme elflord
  set lines=60 columns=108 linespace=0
  if has('gui_win32')
    set guifont=DejaVu_Sans_Mono:h10:cANSI
  else
    set guifont=DejaVu\ Sans\ Mono\ 10
  endif
endif

if has("gui_running")
  if has("gui_gtk2")
    set guifont=Courier\ New\ 11
  elseif has("gui_photon")
    set guifont=Courier\ New:s11
  elseif has("gui_kde")
    set guifont=Courier\ New/11/-1/5/50/0/0/0/1/0
  elseif has("x11")
    set guifont=-*-courier-medium-r-normal-*-*-180-*-*-m-*-*
  else
    set guifont=Courier_New:h11:cDEFAULT
  endif
endif


