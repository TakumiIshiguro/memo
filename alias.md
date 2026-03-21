# Alias Memo

`.bash_aliases` を編集する:

```bash
vi .bash_aliases
```

## Shell

```bash
alias reload='exec $SHELL -l'
alias bashrc='source ~/.bashrc'
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'
alias bag='cd ~/rosbag/'
alias co='code .'
alias cb='colcon build --symlink-install'
alias cbci='colcon build --symlink-install'
alias cbcl='rm -rf build/ install/ log/ && colcon build --symlink-install'
alias ls='ls --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias grep='grep --color=auto'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias off='poweroff'
alias re='reboot'
```

## Git Alias
```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```
