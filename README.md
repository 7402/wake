## wake

---

### Description

This is a minimalist 2-line shell script using Unix utilities to send a local wake-on-lan (WOL) packet.

### Usage

1. Edit the script to change 00:00:00:00:00:00 to the MAC address of the computer to be woken.
2. Run the script.
```
./wake
```

### Install

This script uses the `ncat` version of the netcat utility, which is part of the [nmap](https://nmap.org) package.
You may need to install it.
 
* macOS

Download and install the nmap package following these [instructions](https://nmap.org/book/inst-macosx.html). 

* RedHat family

```
sudo yum install nmap
```

* Debian family

```
sudo apt-get install nmap
```

### Notes

It may be possible to replace `ncat -w1 -u` with `nc -w1 -u -b` in the script,
depending on the [version](https://unix.stackexchange.com/questions/368155/what-are-the-differences-between-ncat-nc-and-netcat#368160) of `nc` that you have. Note, however, that the older BSD version of `nc` on macOS **will not** work.

It is possible accomplish the same thing by writing a python or perl program instead of using ncat.

It is possible accomplish the same thing by using socat instead of using ncat.

Coolest alternative would be if this worked `> /dev/udp/255.255.255.255/9` but it [doesn't](https://unix.stackexchange.com/questions/217613/bash-permission-denied-when-trying-to-echo-data-directly-to-network).
 
The computer to be woken must be on the same local network as the computer that is doing the waking.
If it isn't, you'll need to change the local broadcast address (255.255.255.255) to a
subnet-specific broadcast address (such as 172.16.1.255).

### License

Unlicense
