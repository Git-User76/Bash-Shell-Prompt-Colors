# GREEN color to regular users and RED color to root

Add to `~/.bashrc` and `/root/.bashrc`.

```shell
# Modern prompt colors
if [[ $EUID -eq 0 ]]; then
    # Root prompt - RED theme
    PS1='\[\033[31m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[31m\]❯\[\033[0m\] '
else
    # Regular user prompt - CYAN/GREEN theme
    PS1='\[\033[36m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[32m\]❯\[\033[0m\] '
fi
```
