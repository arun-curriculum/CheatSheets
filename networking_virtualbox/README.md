# VirtualBox Networking

1. Go to Settings -> Network
2. Make adapter 1 a NAT adapter
3. Make adapter 2 a host-only adapter vboxnet0
4. Edit the /etc/network/interfaces and make sure it looks like the following:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# Host only
auto eth1
iface eth1 inet dhcp
```

5. Reboot the machine