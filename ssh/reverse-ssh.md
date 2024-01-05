# Setting up Reverse SSH from Raspberry Pi to Remote Server

This guide helps you establish a reverse SSH connection from your Raspberry Pi to a remote server on port 6543.

## Prerequisites
- Raspberry Pi with SSH enabled
- Remote server accessible via SSH

## Steps

### 1. Install SSH Server on Remote Server
If not already installed, ensure that an SSH server is running on your remote server.

### 2. Generate SSH Keys (if not done already)
If you haven't generated SSH keys on your Raspberry Pi, do so by running:
```bash
ssh-keygen -t rsa -b 4096
```
Follow the prompts to create a new SSH key pair.

### 3. Copy Public Key to Remote Server
Use `ssh-copy-id` to copy the public key to the remote server. Replace `<remote_server_username>` and `<remote_server_ip>` with your remote server's username and IP address.
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub <remote_server_username>@<remote_server_ip>
```
Enter your password when prompted.

### 4. Configure Reverse SSH
On your Raspberry Pi, create a reverse SSH tunnel using the following command. Replace `<remote_server_username>`, `<remote_server_ip>`, and `6543` with your remote server's username, IP address, and port respectively.
```bash
ssh -fN -R 6543:localhost:22 <remote_server_username>@<remote_server_ip>
```
This command creates a reverse tunnel from the remote server's port 6543 to your Raspberry Pi's SSH port 22.

### 5. Test the Connection
Try SSHing from the remote server back to your Raspberry Pi using the established tunnel:
```bash
ssh -p 6543 localhost
```
This command connects you to your Raspberry Pi via the reverse SSH tunnel.

### 6. Automate SSH Tunnel (Optional)
To automatically establish the SSH tunnel on boot, add the SSH command from step 4 to a script or use `crontab` to schedule it.

### 7. Persistence (Optional)
Ensure the SSH tunnel remains active by setting up monitoring scripts or using utilities like autossh to automatically restart the tunnel if it goes down.
