# Checking the current DNS server
Before setting the DNS server to 8.8.8.8, you may want to check the current DNS server. To do this, open the terminal and type the following command:
```bash
cat /etc/resolv.conf
```
This command will display the current DNS server.

# Editing the /etc/resolv.conf file
The /etc/resolv.conf file is a configuration file that contains information about the DNS servers to use. To set the DNS server to 8.8.8.8, you need to edit this file. To do this, open the terminal and type the following command:
```bash
sudo nano /etc/resolv.conf
```
This command will open the /etc/resolv.conf file in the nano text editor. Then, add the following line at the top of the file:
```bash
nameserver 8.8.8.8
```
Save the changes and exit the text editor.
