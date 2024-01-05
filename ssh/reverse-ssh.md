# Setting up Reverse SSH from Raspberry Pi to Remote Server

This guide helps you establish a reverse SSH connection from your Raspberry Pi to a remote server on port 6543.

## Prerequisites
- Raspberry Pi with SSH enabled
- Remote server accessible via SSH

## Steps

### 1. Install SSH Server on Remote Server
If not already installed, ensure that an SSH server is running on your remote server.

### 2. Configure Reverse SSH
On your Raspberry Pi, create a reverse SSH tunnel using the following command. Replace `<remote_server_username>`, `<remote_server_ip>`, and `6543` with your remote server's username, IP address, and port respectively.
```bash
ssh -fN -R 6543:localhost:22 <remote_server_username>@<remote_server_ip>
```
This command creates a reverse tunnel from the remote server's port 6543 to your Raspberry Pi's SSH port 22.

### 3. Test the Connection
Try SSHing from the remote server back to your Raspberry Pi using the established tunnel:
```bash
ssh -p 6543 localhost
```
This command connects you to your Raspberry Pi via the reverse SSH tunnel.

### 4. Automate SSH Tunnel (Optional)
To automatically establish the SSH tunnel on boot, add the SSH command from step 4 to a script or use `crontab` to schedule it.

### 5. Persistence (Optional)
Ensure the SSH tunnel remains active by setting up monitoring scripts or using utilities like autossh to automatically restart the tunnel if it goes down.
