## IP Tables

[IP tables](https://linux.die.net/man/8/iptables)  is used to set up, maintain, and inspect the tables of IP packet filter rules in the Linux kernel. Several different tables may be defined. Each table contains a number of built-in chains and may also contain user-defined chains.

## Installing IP tables

Before installation, Let us first update our packages using the command:
```
apt install updates -y
```
<br>

Next, let's install IP tables using the command:
```
apt install iptables -y
```
<br>

## IP Tables Rules and Policy

To check the list of policies and rules, run the command:
```
iptables -L --line-numbers
```
<br>

## Adding a Rule

For this instance. Let us create a rule to block a specific to remotely SSH on our system. To do that, We will use the command:
```
iptables -A INPUT -s <IP ADDRESS> -p TCP --dport 22 -j DROP
```
<br>

***Explaination:***

```-A``` refers to the chain rule that we will be using which in this case is ```INPUT ```.

```-s``` refers to the source address.

```-p``` refers to the protocol that we will be using which is ```TCP```.

```--dport``` refers to the destination which in this case is port 22.

```-j``` refers to the action of the rule in this case is ```DROP```.
<br>

## Deleting a Rule

To delete a rule, we can run the command:
```
iptables -D INPUT <CHAIN RULE NUMBER>
```
<br>

