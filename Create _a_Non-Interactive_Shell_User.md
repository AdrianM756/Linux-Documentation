## Non-Interactive Shell User

Non-Interactive Shell User means setting up an account that can’t log in to a terminal or interact with the system directly. Non-Interactive Shell is is commonly used for:
<br>

**System users** - Accounts that are created for services (like Apache or MySQL) that don’t require login access.

**Security** - To prevent unauthorized shell access while still allowing the user to own files or run processes.
<br>
<br>

To Create a user with non-interactive shell, we can use the command:
<br>
```
sudo useradd -s /sbin/nologin <USERNAME>
```
<br>

*Explaination:*

* ```sudo``` Runs the command with superuser (admin) privileges.

* ```useradd``` Creates a new user.

* ```-s``` or ```--shell``` refers to the name of the user's login shell. 

* ```/sbin/nologin``` Sets the user's login shell to ```/sbin/nologin```. By setting the shell to ```/sbin/nologin```, you're telling the system that this user should not be allowed to log in interactively.
<br>
<br>

## Verify if a user in Non-Interactive Shell

To verify that a user is in Non-Interactive shell, we can use the command:
<br>
```
cat /etc/passwd | grep <USERNAME>
```
<br>

You will then have this similar output:
<br>
```
username:x:1001:1001::/home/username:/sbin/nologin
```
<br>
<br>

An alternative way is to use the [getent](https://man7.org/linux/man-pages/man1/getent.1.html) command:
<br>
```
getent passwd <USERNAME>
```
<br>

This will return the same line from ```/etc/passwd``` and you can inspect the shell at the end.
<br>
<br>

