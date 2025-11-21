# Bash Shell Prompt Colors
Personal script to customize bash shell prompt colors. Just copy and paste the code.

<br>

## Installation

### 🟢 Regular User Prompt Colors
```shell
# Ensure regular user's .bashrc sources .bashrc.d
grep -q "bashrc.d" ~/.bashrc || echo '
# Source custom scripts from .bashrc.d/
if [ -d ~/.bashrc.d ]; then
    for i in ~/.bashrc.d/*.sh; do
        [ -r "$i" ] && source "$i"
    done
fi' >> ~/.bashrc

# Create bashrc.d drop-in directory (if not exist)
mkdir -p ~/.bashrc.d/

# Create script in drop-in directory
cat << 'EOF' > ~/.bashrc.d/shell_color.sh
#!/bin/bash
# Regular user prompt - GREEN color
PS1='\[\033[32m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[32m\]❯\[\033[0m\] '
EOF

# Apply changes to current session
source ~/.bashrc
```

### 🔴 For Root User Prompt Colors
```shell
# Ensure root's .bashrc sources the .bashrc.d directory
sudo bash -c 'grep -q "bashrc.d" /root/.bashrc || echo "
# Source custom scripts from .bashrc.d/
if [ -d ~/.bashrc.d ]; then
    for i in ~/.bashrc.d/*.sh; do
        [ -r \"\$i\" ] && source \"\$i\"
    done
fi" >> /root/.bashrc'

# Create bashrc.d drop-in directory (if not exist)
sudo mkdir -p /root/.bashrc.d/

# Create script in drop-in directory
sudo bash -c 'cat << "EOF" > /root/.bashrc.d/shell_color.sh
#!/bin/bash
# Root prompt - RED color
PS1='"'"'\[\033[31m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[31m\]❯\[\033[0m\] '"'"'
EOF'
```

### 🟢🔴 BOTH IN ONE COMMAND
```
# Ensure root's .bashrc sources the .bashrc.d directory
sudo bash -c 'grep -q "bashrc.d" /root/.bashrc || echo "
# Source custom scripts from .bashrc.d/
if [ -d ~/.bashrc.d ]; then
    for i in ~/.bashrc.d/*.sh; do
        [ -r \"\$i\" ] && source \"\$i\"
    done
fi" >> /root/.bashrc'

# Create bashrc.d drop-in directory (if not exist)
sudo mkdir -p /root/.bashrc.d/

# Create script in drop-in directory
sudo bash -c 'cat << "EOF" > /root/.bashrc.d/shell_color.sh
#!/bin/bash
# Root prompt - RED color
PS1='"'"'\[\033[31m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[31m\]❯\[\033[0m\] '"'"'
EOF'

# Ensure regular user's .bashrc sources .bashrc.d
grep -q "bashrc.d" ~/.bashrc || echo '
# Source custom scripts from .bashrc.d/
if [ -d ~/.bashrc.d ]; then
    for i in ~/.bashrc.d/*.sh; do
        [ -r "$i" ] && source "$i"
    done
fi' >> ~/.bashrc

# Create bashrc.d drop-in directory (if not exist)
mkdir -p ~/.bashrc.d/

# Create script in drop-in directory
cat << 'EOF' > ~/.bashrc.d/shell_color.sh
#!/bin/bash
# Regular user prompt - GREEN color
PS1='\[\033[32m\]\u@\h\[\033[0m\] \[\033[34m\]\w\[\033[0m\] \[\033[32m\]❯\[\033[0m\] '
EOF

# Apply changes to current session
source ~/.bashrc
```

---
<br>

## DONE - When Do Changes Take Effect?
🟢 **For Regular Users**
- **Immediate visibility after:**
    - Running `source ~/.bashrc` in current terminal.
    - Running `bash` to start a subshell.
- **Automatic visibility in:**
    - New terminal windows/tabs.
    - New SSH sessions.
    - After logout and login.

🔴 **For Root User**
- **Immediate visibility after:**
    - Running `source ~/.bashrc` while already in root shell.
    - Executing `exec bash` while already in root shell.
- **Automatic visibility when:**
    - Starting new root session with `sudo -i`.
    - Using `su -` (if root password is set).
    - Opening new terminal/SSH session as root user.
