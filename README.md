Simple bash script to customize your shell prompt with color-coded user identification.

<br>

## Prerequisites
- Bash shell (version 4.0+).
- Terminal with color support.
- Write access to home directory.

---
<br>

## Installation
### Create Drop-In Configuration Directory
- Create drop-in directory for custom scripts read by `.bashrc` (default in many distros).
- If `.bashrc` is not configured to read `.bashrc.d/` scripts make the required changes.

**For Regular Users:**
```shell
mkdir -p ~/.bashrc.d/
```

**For System-Wide (Root) Access:**
```shell
sudo mkdir -p /root/.bashrc.d/
```

<br>

### Create Script In Drop-In Directory
**Regular User Configuration**
```shell
cat << 'EOF' > ~/.bashrc.d/shell_color.sh
#!/bin/bash
# Modern prompt colors - Visual user identification
if [[ $EUID -eq 0 ]]; then
    # Root prompt - RED theme
    PS1='\[\033[31m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[31m\]❯\[\033[0m\] '
else
    # Regular user prompt - CYAN/GREEN theme
    PS1='\[\033[36m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[32m\]❯\[\033[0m\] '
fi
EOF
```

**Root Configuration (for sudo sessions)**
```shell
sudo cat << 'EOF' > /root/.bashrc.d/shell_color.sh
#!/bin/bash
# Modern prompt colors - Visual user identification
if [[ $EUID -eq 0 ]]; then
    # Root prompt - RED theme
    PS1='\[\033[31m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[31m\]❯\[\033[0m\] '
else
    # Regular user prompt - CYAN/GREEN theme
    PS1='\[\033[36m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[32m\]❯\[\033[0m\] '
fi
EOF
```

<br>

## Implement Changes
- Reload your shell configuration to implement changes.
- Alternatively, start a new terminal session.
```shell
source ~/.bashrc
```

<br>

## DONE
After executing the code, the colors of the shell prompt will change.
