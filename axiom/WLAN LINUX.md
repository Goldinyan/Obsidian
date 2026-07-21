

WLAN doesn't work - Linux



Check Hardware & Drivers, is the WLAN-Card getting registered by Linux or is a kernel driver being loaded?

```bash
lspci -nnk | grep -iA3 net # logs PCI Devices (intern cards)
                           # shows networkcards and loaded kernel
                           # drivers for it 
                           # look for "Kernel driver in use:
                           # iwlwifi / ath9k
                           
lsusb # logs USB-Devices (WLAN-Dongles) 

dmesg | grep -i -E "wifi|wlan|firmware" # logs errors in kernel logs
```

Is it maybe blocked by soft- hardware?

```bash
rfkill list # shows if it is blocked
            # -> Soft blocked: yes / Hard blocked: yes
sudo rfkill unblock wifi # if hardblocked use physical button or fn key 
```

Check if Network-Interface is aktiv

```bash
ip link # show interface look for wlan0 or wlp3s0
sudo ip ling set <interface_name> up # activate manually
```

If it has a NetworkManager use it:

```bash
nmtui
```

If not use the CLI nmcli

```bash
nmcli device wifi list # scans wlan in the area
```

```bash
nmcli device wifi connect "SSID_NAME" password "password" # Connect to one
```


If connected, but nothing loads, it is possibly the fault of IP-Allocation or DNS

```bash
ip a # check ip-address
```

If the WLAN-Interface has an IP like 192.168.x.x?

```bash
ping -c 3 8.8.8.8 # ping directly (tests without DNS)
ping -c 3 google.com # ping domain
```

If the ping to 8.8.8.8 works but domain not, then it is possibly the dns server configured wrong, then look into `cat etc/resolv.conf`


