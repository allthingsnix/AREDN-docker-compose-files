# Docker Installation

Official Docker intalltion steps can be found on [docs.docker.com](https://docs.docker.com/engine/install/). 

:warning: WARNING

Any steps found here are a quick cheat sheet guide and may or may not reflect the current installation process.

## Ubuntu Linux

1. Run the following command to remove any preinstalled conflicting packages
  ```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
2. Setup Dockers apt repository
  ```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
  ```
3. Install the latest version of docker
  ```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```

## Debian Linux

1. Run the following command to remove any preinstalled conflicting packages
  ```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
  ```
2. Setup Dockers apt repository
  ```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
  ```
3. Install the latest version of docker
  ```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```

## Raspberry Pi OS

:exclamation: IMPORTANT

This installation instruction refers to the 32-bit (armhf) version of Raspberry Pi OS. If you're using the 64-bit (arm64) version, follow the instructions for [Debian](#debian-linux).


1. Run the following command to remove any preinstalled conflicting packages
  ```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
  ```
2. Setup Dockers apt repository
  ```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/raspbian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Set up Docker's APT repository:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/raspbian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
  ```
3. Install the latest version of docker
  ```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```

## CentOS Linux

1. Remove old versions
  ```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
  ```
2. Add Docker yum repository
  ```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
  ```
3. Install the latest version of docker
  ```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
4. Start the Docker service and enable it to start on boot
  ```
sudo systemctl enable docker --now
  ```

## Fedora

1. Remove old versions
  ```
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
  ```
2. Add Docker dnf repository
  ```
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
  ```
3. Install the latest version of docker
  ```
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
4. Start the Docker service and enable it to start on boot
  ```
sudo systemctl enable docker --now
  ```

## SLES
1. Add the OpenSuse SELinux zypper repository
  ```
opensuse_repo="https://download.opensuse.org/repositories/security:/SELinux/openSUSE_Factory/security:SELinux.repo"
sudo zypper addrepo $opensuse_repo
  ```
2. Remove old versions
  ```
sudo zypper remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine \
                  runc
  ```
3. Add the Docker zypper repository
  ```
sudo zypper addrepo https://download.docker.com/linux/sles/docker-ce.repo
  ```
4. Install the latest version of docker
  ```
sudo zypper install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
5. Start the Docker service and enable it to start on boot
  ```
sudo systemctl enable docker --now
  ```

## RHEL (s390x)
:exclamtion: IMPORTANT
The installation instructions on this page refer to packages for RHEL on the s390x architecture (IBM Z). Other architectures, including x86_64, aren't yet supported for RHEL.

For other architectures, you may be able to install the CentOS packages. Refer to the [CentOS Installation](#centos-linux)

1. Remove old versions
  ```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine \
                  podman \
                  runc
  ```
2. Add Docker yum repository
  ```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo
  ```
3. Install the latest version of docker
  ```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
  ```
4. Start the Docker service and enable it to start on boot
  ```
sudo systemctl enable docker --now
  ```

