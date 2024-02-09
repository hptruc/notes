# Prerequisites
The computer has activated Windows Subsystem for Linux (WSL) and installed a Linux OS (e.g. Ubuntu) within WSL.

# Step 1 - Installing Docker
First, update your existing list of packages:
```bash
sudo apt update
```
If unable to access software packages from the update server, try changing the DNS of the Linux OS to 8.8.8.8

Next, install a few prerequisite packages which let apt use packages over HTTPS:
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

Then add the GPG key for the official Docker repository to your system:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Add the Docker repository to APT sources:
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update your existing list of packages again for the addition to be recognized:
```bash
sudo apt update
```

Make sure you are about to install from the Docker repo instead of the default Ubuntu repo:
```bash
apt-cache policy docker-ce
```

Install Docker
```bash
sudo apt install docker-ce
```

Docker should now be installed, the daemon started, and the process enabled to start on boot. Check that it’s running:

```bash
sudo systemctl status docker
```
If systemctl is disabled, enable it following this guideline: [Systemd Support in WSL](https://devblogs.microsoft.com/commandline/systemd-support-is-now-available-in-wsl/)

The output should be similar to the following, showing that the service is active and running:
```
docker.service - Docker Application Container Engine
    Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
    Active: active (running) since Fri 2022-04-01 21:30:25 UTC; 22s ago
    ...
```

# Step 2 - Executing the Docker Command Without Sudo (Optional)
Add your username to the docker group
```bash
sudo usermod -aG docker ${USER} 
```

To apply the new group membership, log out of the server and back in, or type the following:
```bash
su - ${USER}
```

Confirm that your user is now added to the docker group by typing:
```bash
groups
```
```
Output
sammy sudo docker
```

If you need to add a user to the docker group that you’re not logged in as, declare that username explicitly using:
```bash
sudo usermod -aG docker username # replace username by your username
```

## References
- [Docker Installation WSL Guide](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)
- [Docker Documentation](https://docs.docker.com/)