1. Use sublime as text editor with ``edit`` command:

``alias edit="/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl"``


2. Use colors in Terminal:

``nano .bash_profile``

```
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
alias ls='ls -GFh'
```
