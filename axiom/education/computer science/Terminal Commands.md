#status/done

#### File & Directory Commands
```bash
pwd             # Show current directory
ls              # List files
ls -lha         # Detailed file list
cd folder       # Change directory
mkdir foo       # Create directory
rmdir foo       # Remove empty directory
rm file.txt     # Delete file
rm -rf bar      # Delete directory
cp a.txt b.txt  # Copy file
mv a.txt b.txt  # Move/Rename file
```


#### User Commands
```bash
whoami          # Current user
id              # User information
passwd          # Change passowrd
sudo su         # Switch to root
adduser user    # Create user
```


#### Process Management 
```bash
ps aux          # Running processes 
top             # System monitor 
htop            # Interacitve monitor
kill PID        # Kill process
killall app     # Kill by name
```


#### Network Commands 
```bash
ifconfig        # Network interfaces
ip a            # Show IP address 
ping google.com # continusly send packets to url
netstat         # Shows connections
traceroute google.com # Tracks the route of a packet - very cool
```
#### File Viewing
```bash
cat file.txt
less file.txt
head file.txt
tail file.txt
nano file.txt
vim file.txt
```
#### Information Gathering
```bash
nmap target.com
whois target.com
dig google.com
nslookpu google.com
```
