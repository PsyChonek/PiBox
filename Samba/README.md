https://github.com/ServerContainers/samba

List disks
```
fdisk
```

Install gparted
```
sudo apt-get install gparted
```

```
sudo gparted
```

Format the drive

Create a new partition table
```
sudo mkfs.ext4 /dev/sdb1
```

Make mount points for the drives
```
sudo mkdir /mnt/sdb1
```

Mount the drive
```
sudo mount /dev/sdb1 /mnt/sdb1
```