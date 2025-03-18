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

**Note**: This module supports only ubuntu noble 24.04.

## Steps to run

- Download docker packages

  ```bash
  mkdir -p roles/docker/files

  wget https://download.docker.com/linux/ubuntu/dists/noble/pool/stable/amd64/containerd.io_1.7.25-1_amd64.deb -O roles/docker/files/containerd.deb
  wget https://download.docker.com/linux/ubuntu/dists/noble/pool/stable/amd64/docker-buildx-plugin_0.21.0-1~ubuntu.24.04~noble_amd64.deb -O roles/docker/files/docker-buildx-plugin.deb
  wget https://download.docker.com/linux/ubuntu/dists/noble/pool/stable/amd64/docker-ce-cli_28.0.0-1~ubuntu.24.04~noble_amd64.deb -O roles/docker/files/docker-ce-cli.deb
  wget https://download.docker.com/linux/ubuntu/dists/noble/pool/stable/amd64/docker-ce_28.0.0-1~ubuntu.24.04~noble_amd64.deb -O roles/docker/files/docker-ce.deb
  wget https://download.docker.com/linux/ubuntu/dists/noble/pool/stable/amd64/docker-compose-plugin_2.33.0-1~ubuntu.24.04~noble_amd64.deb -O roles/docker/files/docker-compose-plugin.deb
  ```

- Run playbook

  ```bash
  ansible-playbook -i inventories -e @group_vars/main.yaml playbook.yaml
  ```