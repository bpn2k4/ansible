# Docker Ansible

This module installs docker on target machine (offline mode).

Docker components:

| Components            | Version |
| --------------------- | ------- |
| containerd            | 1.7.25  |
| docker-ce             | 28.0.0  |
| docker-ce-cli         | 28.0.0  |
| docker-buildx-plugin  | 0.21.0  |
| docker-compose-plugin | 2.33.0  |

**Note**: This module supports only ubuntu noble 24.04, jammy 22.04, focal 20.04.

## Steps to run

- Download docker packages
  - Ubuntu 20.04
    ```bash
    mkdir -p roles/docker/files
    wget https://github.com/bpn2k4/ansible/releases/download/docker-28.0.0/docker-focal-28.0.0.tar.gz -O roles/docker/files/docker.tar.gz
    tar -zxvf roles/docker/files/docker.tar.gz -C roles/docker/files
    ```

  - Ubuntu 22.04
    ```bash
    mkdir -p roles/docker/files
    wget https://github.com/bpn2k4/ansible/releases/download/docker-28.0.0/docker-jammy-28.0.0.tar.gz -O roles/docker/files/docker.tar.gz
    tar -zxvf roles/docker/files/docker.tar.gz -C roles/docker/files
    ```

  - Ubuntu 24.04
    ```bash
    mkdir -p roles/docker/files
    wget https://github.com/bpn2k4/ansible/releases/download/docker-28.0.0/docker-noble-28.0.0.tar.gz -O roles/docker/files/docker.tar.gz
    tar -zxvf roles/docker/files/docker.tar.gz -C roles/docker/files
    ```

- Run playbook

  ```bash
  ansible-playbook -i inventories -e @group_vars/main.yaml playbook.yaml
  ```