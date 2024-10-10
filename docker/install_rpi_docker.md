# Install docker in a Rapberry Pi

To install Docker on your Raspberry Pi using the convenience script from Docker's website, you can use the following steps:

### 1. **Update Your System**
Before you start, ensure your Raspberry Pi OS is up to date:

```bash
sudo apt-get update
sudo apt-get upgrade
```

### 2. **Download the Docker Installation Script**
Run the following command to download Docker's official installation script using `curl`:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
```

### 3. **Run the Docker Installation Script**
Once the script is downloaded, execute it to install Docker:

```bash
sudo sh get-docker.sh
```

The script will automatically detect your system's architecture and install the appropriate version of Docker for your Raspberry Pi.

### 4. **Add Your User to the Docker Group**
After the installation completes, add your current user to the `docker` group to manage Docker without needing `sudo`:

```bash
sudo usermod -aG docker $USER
```

Then, log out and log back in to apply the changes, or run:

```bash
newgrp docker
```

### 5. **Verify the Installation**
Check if Docker is installed successfully by running:

```bash
docker --version
```

You can also run a test container to ensure Docker is working:

```bash
docker run hello-world
```

### 6. **Enable Docker to Start on Boot (Optional)**
If you want Docker to start automatically when the Raspberry Pi boots:

```bash
sudo systemctl enable docker
```

That's it! Docker should now be installed and ready for use on your Raspberry Pi.
