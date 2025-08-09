## SELinux

SELinux (Security-Enhanced Linux) is a security module for the Linux kernel that enables the implementation of access control policies, including mandatory access control (MAC) mechanisms.
<br>

## Installation

On this demo, We will be installing ```SELinux``` on a ```CentOS 9``` machine.
<br>

<details>
<summary>First, let's update the system package.</summary>

```
yum update -y
```
</details>

<details>
<summary>Next, Let' install <b>SELinux</b>.</summary>
  
```
yum install seLinux* -y
```
</details>

<details>
<summary>To verify that it's already, we can use the command:</summary>

```
whereis selinux | grep /etc
```
</details>

<details>
<summary>You can check the configuration file on the <mark>/etc/selinux</mark> directory.</summary>

```
cd /etc/selinux
```
</details>  





