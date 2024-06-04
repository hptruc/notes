# WSL Configuration
**1. Edit the WSL configuration file:**
```bash
  sudo nano /etc/wsl.conf
```
**2. Add the following lines:**
```bash
[boot]
command="service docker start"
```
**3. Save and exit the editor (Ctrl+X, then Y, then Enter in nano).**
**4. Exit wsl and restart by command:**
```bash
wsl --shutdown
```
**5. Access to Wsl and verify by command**
```bash
docker info
```
