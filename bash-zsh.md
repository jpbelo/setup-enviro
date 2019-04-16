1. Use nano as git editor

`git config --global core.editor "nano -w"`


2.Use colors in Terminal and call bashrc into bash_profile

``nano .bash_profile``

```
xport PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
alias ls='ls -GFh'

[[ -r ~/.bashrc ]] && . ~/.bashrc
```
