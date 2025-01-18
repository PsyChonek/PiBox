# CHATGPT - NOT TESTED

### **Step 1: Format Disk 2**
1. **Launch `parted`**  
   Start by identifying and opening the second disk (`/dev/sdb`):
   ```
   sudo parted /dev/sdb
   ```

2. **Create a Partition Table**  
   Inside the `parted` prompt, create a new partition table (GPT is recommended):
   ```
   (parted) mklabel gpt
   ```

3. **Create a Partition**  
   Create a new partition spanning the entire disk:
   ```
   (parted) mkpart primary ext4 0% 100%
   ```

4. **Exit `parted`**  
   ```
   (parted) quit
   ```

5. **Format the Partition**  
   Format the newly created partition as ext4:
   ```
   sudo mkfs.ext4 /dev/sdb1
   ```

---

### **Step 2: Set Up RAID 1**
Use `mdadm` to configure the RAID array.

1. **Install `mdadm`**  
   If not already installed:
   ```
   sudo apt update
   sudo apt install mdadm
   ```

2. **Create the RAID 1 Array**  
   Set up RAID 1 with disk 1 and disk 2:
   ```
   sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
   ```
   Replace `/dev/sda1` and `/dev/sdb1` with the correct partitions for your disks.

3. **Monitor the RAID Sync**  
   Check the synchronization process:
   ```
   cat /proc/mdstat
   ```

4. **Save the RAID Configuration**  
   Add the RAID details to the configuration file:
   ```
   sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
   sudo update-initramfs -u
   ```

---

### **Step 3: Set Up Disk Health Monitoring**
1. **Install SMART Monitoring Tools**  
   Install `smartmontools`:
   ```
   sudo apt install smartmontools
   ```

2. **Enable SMART for Each Disk**  
   Enable SMART monitoring on both disks:
   ```
   sudo smartctl -s on /dev/sda
   sudo smartctl -s on /dev/sdb
   ```

3. **Set Up Alerts**  
   Configure `/etc/smartd.conf` to send alerts:
   ```
   /dev/sda -m your-email@example.com
   /dev/sdb -m your-email@example.com
   ```
   Restart the SMART monitoring service:
   ```
   sudo systemctl restart smartd
   ```

---

### Summary of Commands
Here’s a condensed list of commands:
```bash
# Step 1: Format disk 2
sudo parted /dev/sdb mklabel gpt
sudo parted /dev/sdb mkpart primary ext4 0% 100%
sudo mkfs.ext4 /dev/sdb1

# Step 2: Set up RAID 1
sudo apt install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
cat /proc/mdstat
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
sudo update-initramfs -u

# Step 3: Monitor disk health
sudo apt install smartmontools
sudo smartctl -s on /dev/sda
sudo smartctl -s on /dev/sdb
sudo nano /etc/smartd.conf  # Add email alerts
sudo systemctl restart smartd
```

This CLI workflow mirrors what you’d achieve in GParted GUI. If you'd like a script for automation, let me know!