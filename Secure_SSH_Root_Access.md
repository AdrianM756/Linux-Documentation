## Secure SSH Root Access

By default, SSH Root access is enabled. Because the username is always ```root``` and the access rights are unlimited and has the highest privilege, this account is the most valuable target for Attackers. There are a lot of bots scanning the Internet for systems with exposed SSH ports. If they find one, they will attempt to login using common usernames and try to guess the password.
<br>

To disable SSH Root access, edit and navigate the ````/etc/ssh/sshd_config```` using ```vi```,```vim```, ```nano``` or other text editor tools. For Example:
<br>
```
nano /etc/ssh/sshd_config
```
<br>

Look for ```PermitRootLogin yes```. edit it to ```PermitRootLogin no```. Save the changes once done.
<br>

Next, Restart the SSH service using this command:
```
systemctl restart sshd
```
<br>



