# Running Docker without sudo

## Prerequisites
- Docker must be installed on your system.
- You must have sudo privileges on your system to modify user groups.

## Step 1: Create the Docker Group (if it does not exist)
1. **Open a Terminal**.

2. **Check if the Docker Group Exists**:
   ```sh
   getent group docker
   ```
   If the group exists, you will see output like `docker:x:999:`, and you can skip the next step. If there is no output, proceed to create the group.

3. **Create the Docker Group**:
   ```sh
   sudo groupadd docker
   ```

## Step 2: Add Your User to the Docker Group
1. **Add Your User to the Docker Group**:
   Replace `your_username` with your actual username:
   ```sh
   sudo usermod -aG docker your_username
   ```

## Step 3: Apply the New Group Membership
1. **Log Out and Log Back In**:
   To apply the group membership, you need to log out of your current session and log back in. This can be done by:
   - Logging out and logging back in via the graphical interface.
   - Or, restarting your computer.

   Alternatively, you can use the following command to apply the new group membership without logging out:
   ```sh
   newgrp docker
   ```

## Step 4: Verify That You Can Run Docker Commands Without sudo
1. **Run a Docker Command**:
   ```sh
   docker run hello-world
   ```

   If everything is set up correctly, you should see the following output without needing `sudo`:
   ```
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   ...
   ```

## Conclusion
You have successfully configured your system to run Docker commands without using `sudo`. This makes managing Docker containers easier and more convenient.
