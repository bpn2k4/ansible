# Ansible

## **Table of Contents**
1. [Install Ansible](#1-install-ansible)

## 1. Install Ansible

### Requirements
- The <b>control node</b> (the machine that runs Ansible) must use a Linux-like operating system such as Red Hat, Debian, Ubuntu, macOS, BSDs, or Windows with Windows Subsystem for Linux (WSL). Python must also be installed.

  <b>Recommender OS</b>: Ubuntu 24.04

- The <b>remote node</b> (the machine that will be managed by Ansible) must use a Linux-like operating system such as Red Hat, Debian, Ubuntu, macOS, or BSDs (Windows is not supported). The following must be installed:
  - `openssh-server`
  - `python3` (version ≥ 3.8)

  <b>Recommender OS</b>: Ubuntu 24.04 (which includes Python 3.12).

### Installation instructions
- On macOS:
  ```bash
  brew install pipx
  pipx ensurepath
  sudo pipx ensurepath
  pipx install --include-deps ansible
  pipx install ansible-core
  ```

- On Ubuntu:
  ```bash
  sudo apt update
  sudo apt install pipx
  pipx ensurepath
  sudo pipx ensurepath
  pipx install --include-deps ansible
  pipx install ansible-core
  ```

- On Fedora, RHEL, Centos:
  ```bash
  sudo dnf install pipx
  pipx ensurepath
  sudo pipx ensurepath
  pipx install --include-deps ansible
  pipx install ansible-core
  ```

**Note:** Log out and log back in for the bash environment changes to take effect.

### Granting sudo permissions for ansible
Some ansible tasks require sudo permission. To allow `ansible_user` to use `su` or `sudo` without password. SSH to remote node and run:
```bash
# Replace <username> with the actual user
echo "<username> ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/<username>

# Example for the "ubuntu" user
echo "ubuntu ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ubuntu
```

### Copy SSH key to remote node

It is recommended to copy the SSH key to the remote node.
Otherwise, you may need to:
- Use `ansible_password` or `ansible_ssh_private_key_file` in inventory file.

  Or

- Passing `--password=<password>` or `--private-key=<path_to_private_key_file>` value when run `ansible-playbook`.

To copy SSH key to remote node, run:
```bash
# Replace <username> and <ip_address> with the actual user and IP address
ssh-copy-id <username>@<ip_address>

# Example for the "ubuntu" user
ssh-copy-id ubuntu@192.168.182.150
```
