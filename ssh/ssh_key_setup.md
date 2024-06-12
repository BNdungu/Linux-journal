
# Generating SSH Keys and Setting Them Up on Your Server

## Prerequisites
- A client machine (your local computer)
- Access to the server (via username and password initially)

## Step 1: Generate SSH Keys on Your Client Machine
1. **Open a Terminal**:
   - On Windows, you can use Git Bash, PowerShell, or Command Prompt.
   - On macOS and Linux, open the Terminal.

2. **Generate the SSH Key Pair**:
   Run the following command to generate a new SSH key pair. Replace `your_email@example.com` with your email address:
   ```sh
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```
   This command will create a new SSH key using the RSA algorithm with a 4096-bit key.

3. **Follow the Prompts**:
   - **Enter file in which to save the key**: Press Enter to accept the default location (`/home/your_username/.ssh/id_rsa` or `C:\Users\your_username\.ssh\id_rsa`).
   - **Enter passphrase (empty for no passphrase)**: Enter a secure passphrase or leave it empty for no passphrase.

   Example output:
   ```
   Generating public/private rsa key pair.
   Enter file in which to save the key (/home/your_username/.ssh/id_rsa):
   Enter passphrase (empty for no passphrase):
   Enter same passphrase again:
   Your identification has been saved in /home/your_username/.ssh/id_rsa.
   Your public key has been saved in /home/your_username/.ssh/id_rsa.pub.
   ```

## Step 2: Copy the Public Key to Your Server
1. **Use `ssh-copy-id`** (if available):
   ```sh
   ssh-copy-id username@server_ip_address
   ```
   Replace `username` with your server's username and `server_ip_address` with the server's IP address.

2. **Alternatively, Manually Copy the Key**:
   - **Display the Public Key**:
     ```sh
     cat ~/.ssh/id_rsa.pub
     ```
     Copy the displayed key to your clipboard.

   - **Login to Your Server**:
     ```sh
     ssh username@server_ip_address
     ```

   - **Create `.ssh` Directory and `authorized_keys` File**:
     ```sh
     mkdir -p ~/.ssh
     nano ~/.ssh/authorized_keys
     ```
     
   - **Paste the Public Key**:
     Paste the public key into the `authorized_keys` file. Save and exit the editor (Ctrl+X, then Y, then Enter for nano).

   - **Set Permissions**:
     ```sh
     chmod 700 ~/.ssh
     chmod 600 ~/.ssh/authorized_keys
     ```

## Step 3: Test SSH Connection
1. **Log Out from the Server**:
   ```sh
   exit
   ```

2. **Connect Using SSH Key**:
   ```sh
   ssh username@server_ip_address
   ```

   You should now be able to log in to your server without being prompted for a password.

## Step 4: (Optional) Disable Password Authentication
To enhance security, you can disable password authentication on your server.

1. **Edit the SSH Configuration File**:
   ```sh
   sudo nano /etc/ssh/sshd_config
   ```

2. **Modify the Following Settings**:
   ```sh
   PasswordAuthentication no
   ChallengeResponseAuthentication no
   ```

3. **Restart SSH Service**:
   ```sh
   sudo systemctl restart sshd
   ```

