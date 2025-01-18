# PiBox Setup Guide - Docker

https://docs.docker.com/engine/install/debian/

### Step 1: Update and Install Dependencies

- Update the package list:
  ```
  sudo apt-get update
  ```
- Install required dependencies:
  ```
  sudo apt-get install ca-certificates curl
  ```

### Step 2: Add Docker's GPG Key and Repository

- Create the keyring directory:
  ```
  sudo install -m 0755 -d /etc/apt/keyrings
  ```
- Download and add Docker's GPG key:
  ```
  sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
  ```
- Add Docker's repository:
  ```
  echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```

### Step 3: Install Docker

- Update the package list again:
  ```
  sudo apt-get update
  ```
- Install Docker packages:
  ```
  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
- Verify the installation by running a test container:
  ```
  sudo docker run hello-world
  ```

### Step 4: Add User to Docker Group

- Create the Docker group:
  ```
  sudo groupadd docker
  ```
- Add your user to the Docker group:
  ```
  sudo usermod -aG docker $USER
  ```
- Log out and back in or run the following command to apply the group changes:
  ```
  newgrp docker
  ```
- Verify the setup by running the test container again without `sudo`:
  ```
  docker run hello-world
  ```

