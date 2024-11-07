---
tags:
    - linux
    - rm
    - files
    - permissions
    - qcow2
    - base64
    - split
    - tshark
    - lldp
    - avago
    - dd
    - bash
---

# Helpful-Commands
## Remove many/thousands of files
Sometimes the rm (Remove) command will not work when there are too many files in a folder or will take forever.
You can use a for loop to remove the files in a folder. Just change your directory to the folder where you want to
remove the files and run the below command. **This will delete all files in the directory except folders**
```bash
for i in * ; do rm $i ; done
```

## Remove files older then x
Sometimes you only want to keep x iterations of files for example of zipped backups, so you need to remove all files
older then x days. With the below command you can remove all files older then 5 days.
```bash
find /path/to/files/* -mtime +5 -exec rm {} \;
```

## Search recursive through files with a pattern
Sometimes you need to find all files with a specific pattern, for example a domain or ip-address in a config.
The -r option searche recursive, -n shows the line number for every finding and -w searches for whole words.
```bash
grep -rnw '/path/to/somewhere/' -e 'pattern'
```

## Outbound NAT iptables
With the below command you can NAT your traffic from a routed network via a local interface, in this example all packets from a local network on
LAN gets NATed through the wifi interface.
```bash
sudo iptables -t nat -A POSTROUTING -o wlp2s0 -j MASQUERADE
```

## Set file permissions recursive for every file or folder in a path
**Files**
```bash
find /my/path -type f -exec chmod 0644 {} \;
```

**Folder**
```bash
find /my/path -type d -exec chmod 0755 {} \;
```

## Convert text to base64
```bash
echo -n test | base64
```

## Split large files to smaller ones
Sometimes you need to split a large file into a few smaller ones so you can upload them to systems with a file limitation.
After that you can recreate the source file.
**Split large files**
```bash
split -b 512M large.dat

```
**Recreate the source file**
```bash
cat large1.dat large2.dat > large.dat
```

## Listen on a specific port with tshark
```bash
tshark -f "udp port 162" -i any
```

## Create bootable linux USB key
```bash
sudo dd bs=4M if=/path/to/file.iso of=/dev/sdx status=progress oflag=sync
```

## Show lldp neighbour
With the below command you can see to which switch or device you are connected on the LAN port.
```bash
sudo lldpcli show neighbors
```

## Show all disks in AVAGO raid controller
```bash
storcli /c0 /eall /sall show
```

## Create a zip with all files from a folder via cli
```bash
zip -r myfiles.zip mydir1 mydir2
```

## Create WiFi QR-Code
```bash
qrencode -t png -o ~/filename.png 'WIFI:S:SSID-Name;T:WPA2;P:Password;;'
```

## Clear systemd DNS cache
```bash
sudo systemd-resolve --flush-cache
```

## Show systemd DNS cache statistics
```bash
sudo systemd-resolve --statistics
```

## Test disk performance with dd
The below command writes a 10GB file directory to disk without using RAM as cache.
```bash
dd if=/dev/zero of=/testfile bs=10G count=1 oflag=direct  
```

## Show file permissions as number
```bash
stat -c "%a %n"  file.txt
```

## Create one log file from many
**All Logs**
```bash
for i in * ; do echo $i; cat $i/logs/access_ssl_log >> /tmp/all_access.log ; done
```

**Logs with pattern**
```bash
for i in * ; do echo $i; grep "mykeyword" $i/logs/access_ssl_log >> /tmp/all_access.log ; done
```

## List files by size
** Files and directories**
```bash
du -sh -- *  | sort -rh  # Files and directories, or
```

**Directories only**
```bash
du -sh -- */ | sort -rh  # Directories only
```

## Mount qcow2 image
**Mount**
```bash
sudo guestmount -a /var/lib/libvirt/images/myimage.qcow2 -m /dev/sda1 --ro /mnt/tmp
```

**Unmount**
```bash
sudo guestunmount /mnt/tmp
```

## Delete empty files in folder
```bash
find . -name '*.log' -size 0 -print0 | xargs -0 rm
```

## Forever loop
```bash
while true; do echo something; done
```

## Update dynamic nameserver entry from cli
```bash
nsupdate
server localhost
add myserver.local 3600 A 1.1.1.1
send
```

## Show Output of all commands in Shell script
```bash
sh -x myscript.sh
```

## Show and sort swap usage by process
```bash
for file in /proc/*/status ; do awk '/VmSwap|Name/{printf $2 " " $3}END{ print ""}' $file; done | sort -k 2 -n -r | less
```

## fail2ban
**Show status for jail**
```bash
fail2ban-client status JAILNAME
```

**Unban IP**
```bash
fail2ban-client set JAILNAME unbanip ip
```

**Ban IP**
```bash
fail2ban-client set JAILNAME banip ip
```

## convert iso to qcow2 image
```bash
qemu-img convert -O qcow2 file.iso file.qcow2
```