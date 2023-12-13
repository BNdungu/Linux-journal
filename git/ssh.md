
# Setting up SSH Key for GitHub on Raspberry Pi

This guide will help you set up an SSH key for your GitHub account and not only on a Raspberry Pi but also on a desktop and server linux distro OS.
At the time of documentig this I'm running on the Raspberry Pi OS on a Pi 3B.

### 1. Check for Existing SSH Keys

First, navigate to the `.ssh` directory:

```bash
cd ~/.ssh
ls
```

Note that the raspberry by default doesn't have the .ssh directory and thus must created before running the command above.

```bash 
mkdir -m 700 ~/.ssh
```
mkdir is the command to make a directory. -m 700 tells it to make it with the recommended permissions which prevent other users on the system from browsing it.

Look for `id_rsa` (private key) and `id_rsa.pub` (public key). If they exist, use them. If not, generate a new key.

### 2. Generate SSH Key

Generate a new SSH key specifically for GitHub:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Replace `"your_email@example.com"` with your GitHub email.

### 3. Add SSH Key to SSH Agent

Start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

Add your SSH key to the SSH agent:

```bash
ssh-add ~/.ssh/id_rsa
```

### 4. Add SSH Key to GitHub

Display your public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Copy the output.

- Go to GitHub Settings > SSH and GPG keys.
- Click "New SSH key" or "Add SSH key."
- Paste your key into the "Key" field.
- Give your key a title.
- Click "Add SSH key."

### 5. Test SSH Connection

To test the setup, use:

```bash
ssh -T git@github.com
```