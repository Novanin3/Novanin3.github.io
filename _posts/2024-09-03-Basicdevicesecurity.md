---
title: LAB SECURITY
date : 2024-04-23 03:07:00
category: [CCNA]
---
![Alt text](/assets/img/kioptrix/topology.jpg)


# QUESTIONS
1. Change the hostnames of the router and switch to the appropriate names (R1, SW1).Use the 'hostname' command in global configuration mode

Using the commands i changed the host to "R1"

```bash 
R1#config t
Enter configuration commands, one per line. End with CNTL/Z.
R1(config)#hostname R1

```

2. Configure an unencrypted enable password of 'CCNA' on both devices

 i used `enable password CCNA` to set a password to my router.

```bash
R1#config t
Enter configuration commands, one per line. End with CNTL/Z.
R1(config)#enable password CCNA

```

3. Exit back to user EXEC mode and test the password

GLOBAL CONFIG MODE

```bash 
R1(config)#exit

```

PRIVILLEGE EXEC MODE
```bash
R1#
%SYS-5-CONFIG_I: Configured from console by console

```
USER EXEC MODE 
```bash
R1#exit

```
View the password in the running configuration

## command `show running-config` to see the active configuration file on the device.
```bash
R1>enable
Password: 
R1#show running-config
Building configuration...

Current configuration : 711 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R1
!
!
!
enable password CCNA
!
!
!
!
!
!
ip cef
no ipv6 cef
!
```
5. Ensure that the current password, and all future passwords, are encrypted

# i used `service password-encryption` to encrypt the enabled password CCNA.
```bash
R1#config t
Enter configuration commands, one per line. End with CNTL/Z.
R1(config)#service password-encryption
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console

```
6. View the password in the running configuration

```bash
R1#show running-config
Building configuration...

Current configuration : 716 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
!
!
enable password 7 08026F6028
!
!
!
!
!
!
ip cef
no ipv6 cef
!
```

 Configure a more secure, encrypted enable password of 'Cisco' on both devices

i used `enable secret` as my command to encrypt the enabled password CCNA.

```bash
R1#config t
Enter configuration commands, one per line. End with CNTL/Z.
R1(config)#enable secret Cisco
```


8. Exit back to user EXEC mode and then return to privileged EXEC mode.
Which password do you have to use? 
Answer:`Cisco` 

```bash
R1(config)#exit
R1#
%SYS-5-CONFIG_I: Configured from console by console

R1#exit

```

9. View the passwords in the running configuration.

### ANSWER:
password:enable secret 5 `$1$mERr$YlCkLMcTYWwkF1Ccndtll`.
Password:enable password 7 `08026F6028`

```bash
R1#show running-config
Building configuration...

Current configuration : 763 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
!
!
enable secret 5 $1$mERr$YlCkLMcTYWwkF1Ccndtll.
enable password 7 08026F6028
!
!
!
!
!
!
ip cef
no ipv6 cef
!
```


 What encryption type number is used for the encrypted 'enable password'?
## ANSWER:5 MD5
 What encryption type number is used for the encrypted 'enable secret'?
### ANSWER: Type 7

Save the running configuration to the startup configuration
To save the configuration one can use some commands like :`write,write memory`.
```bash
R1#write
Building configuration...
[OK]
```
Once saved  we use `startup-config` to make sure the configuration will be loaded upon restarting on the device.

```bash
R1#show startup-config
Using 763 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
service password-encryption
!
hostname R1
!
!
!
enable secret 5 $1$mERr$YlCkLMcTYWwkF1Ccndtll.
enable password 7 08026F6028
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
``` 

# TODO

