# PiBox Setup Guide - OS

## Operating System Setup

### Chosen OS

- **Raspberry Pi OS LITE 64-bit**: A minimal version of Raspberry Pi OS without a desktop environment, accessed via SSH.

### Step 1: Install the OS on USB SSD

- Use Raspberry Pi Imager to install the OS on the USB SSD.
- Change configuration settings.

- Also recommended to change boot order to USB SSD. You can flash SD card with Imager select Tools -> Bootloader -> USB Boot.

### Step 2: Configure Power Settings

- Raspberry Pi 5 is picky about its power supply and will not boot with power from the SATA hat.
- Edit the `config.txt` file in the boot partition to force USB power:

  ```
  max_usb_current=1
  ```

### Step 3: Boot and Network Setup

- Boot the Pi with the USB SSD.
- Connect the Raspberry Pi to the network using an Ethernet cable.

## SSH into the Pi

### Step 1: Initial Connection

- Use the command `ssh <PI_IP>` to connect to the Pi.
- Log in using the password set during OS installation with Raspberry Pi Imager.

### Step 2: Configure SSH Keys

1. Create the `.ssh` folder in the home directory:

   ```
   mkdir .ssh
   ```

   Navigate to the folder:

   ```
   cd .ssh
   ```

2. Create an `authorized_keys` file:

   ```
   touch authorized_keys
   ```

   Paste your public key into the `authorized_keys` file.

### Step 3: Set Permissions

- Set the appropriate permissions for the `authorized_keys` file:

  ```
  sudo chmod 644 ~/.ssh/authorized_keys
  sudo chown pi:pi ~/.ssh/authorized_keys
  ```

### Recommended Security Enhancements

- Disable password login and root login in the SSH configuration file:

  ```
  sudo nano /etc/ssh/sshd_config
  ```
