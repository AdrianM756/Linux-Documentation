## Create a temporary user

To create a Temporary user on a linux machine, we can use the command:
```
useradd -e <EXPIRATION DATE> <USERNAME>
```
<br>

**Explaination:** 
* ```useradd``` command that is use to create a user account.
* ```-e``` refers to the expiration date of the account.
<br>

To verify that it takes effect, We can use the [chage](https://man7.org/linux/man-pages/man1/chage.1.html) command:
```
chage -l <USERNAME>
```
<br>


