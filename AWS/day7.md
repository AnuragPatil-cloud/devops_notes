## file system and mounting 
https://www.redhat.com/en/blog/partitions-fdisk

## volume mounting and partation 
- lsblk -- list storage
- fdisk /dev/<storage>


# temporary and permenant mounting 
for temporary mounting use
- mount /dev/xvdf1 /mnt/ebs

for permanent mounting
- vim /etc/fstab
```
/dev/xvdf1  /mnt/ebs  ext4  default 0 0    
```
- mkfs -t ext4 /dev/xvdf1   #to format partition with ext4 file system
- mount -a   #to mount all file systems mentioned in fstab file
