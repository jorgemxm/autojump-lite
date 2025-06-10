autojump is a faster way to navigate your filesystem. It works by
maintaining a database of the directories you use the most from the
command line.

*Directories must be visited first before they can be jumped to.*

---

### Repositories:
- Fork → https://github.com/jorgemxm/shell-autojump
- Source → https://github.com/wting/autojump

---

Installation
------------

### Requirements
-   Python v2.6+ or Python v3.3+
-   Supported shells
    -   bash - first class support
    -   zsh - first class support
    -   fish - community supported

### Manual

Grab a copy of autojump:
```sh
git clone https://github.com/jorgemxm/autojump-lite.git ~/.autojump

# Or without git
curl -LfS# https://github.com/jorgemxm/autojump-lite/archive/refs/heads/main.zip -o autojump.zip
unzip -o autojump.zip -d ~/.autojump && mv ~/.autojump/autojump-lite-main/bin ~/.autojump/
rm -rf ~/.autojump/autojump-lite-main autojump.zip
```

Source file in your shell config
```sh
# Bash → ~/.bash_profile
[ -f ~/.autojump/bin/autojump.bash ] && source ~/.autojump/bin/autojump.bash

# Zsh → ~/.zshrc
[ -f ~/.autojump/bin/autojump.zsh ] && source ~/.autojump/bin/autojump.zsh

# Fish → ~/.config/fish/config.fish
if test -f ~/.autojump/bin/autojump.fish; source ~/.autojump/bin/autojump.fish; end
```

---

Usage
-----

`j` is a convenience wrapper function around `autojump`. Any option that
can be used with `autojump` can be used with `j` and vice versa.

-   Jump To A Directory That Contains `foo`:

        j foo

-   Jump To A Directory That Contains `foo`, Preferring Child Directories:

    You can prioritize child directories over matches in the databases via

        jc foo

-   Open File Manager To Directories (instead of jumping):

    Instead of jumping to a directory, you can open a file explorer
    window (Mac Finder, Windows Explorer, GNOME Nautilus, etc.) to the
    directory instead.

        jo music

    Opening a file manager to a child directory is also supported:

        jco images

-   Using Multiple Arguments:

    Let's assume the following database:

        30   /home/user/mail/inbox
        10   /home/user/work/inbox

    `j in` would jump into /home/user/mail/inbox as the higher
    weighted entry. However you can pass multiple arguments to autojump
    to prefer a different entry. In the above example, `j w in` would
    then change directory to /home/user/work/inbox.

For more options refer to help:

    autojump --help

Entries are saved to:

    # j -s  |  j --stat
    ~/.local/share/autojump/autojump.txt


Known issues
------------

-   autojump does not support directories that begin with `-`.

-   For bash users, autojump keeps track of directories by modifying
    `$PROMPT_COMMAND`. Do not overwrite `$PROMPT_COMMAND`:

        export PROMPT_COMMAND="history -a"

    Instead append to the end of the existing \$PROMPT\_COMMAND:

        export PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ;} history -a"

Authors
-------

autojump was originally written by Joël Schaerer, and currently
maintained by William Ting.

Copyright
---------

Copyright © 2016 Free Software Foundation, Inc. License GPLv3+: GNU GPL
version 3 or later <http://gnu.org/licenses/gpl.html>. This is free
software: you are free to change and redistribute it. There is NO
WARRANTY, to the extent permitted by law.
