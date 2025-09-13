# Ansible Installation and Configuration Guide

This repository contains Ansible-related files for automating infrastructure management, including Docker and Jenkins installations.

## Installing Ansible on Ubuntu

The repository provides a shell script for installing Ansible on Ubuntu systems. The script supports two installation methods:

1. **Ubuntu Repository** (stable version)
2. **Official Ansible PPA** (newer version, default)

### Installation Steps

1. Clone this repository or download the files
2. Navigate to the ansible-files directory
3. Make the script executable and run it with sudo:

```bash
chmod +x ansible.sh
sudo ./ansible.sh
```

### Installation Options

By default, the script installs Ansible from the official PPA. If you prefer to use the Ubuntu repository version, set the `USE_PPA` environment variable to 0:

```bash
sudo USE_PPA=0 ./ansible.sh
```

## SSH Key Configuration

After installing Ansible, you'll need to configure SSH keys for connecting to remote hosts. The repository includes a playbook for pushing SSH keys to servers.

### Generate SSH Keys

If you don't have SSH keys yet, generate them:

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Push SSH Keys to Servers

Use the provided playbook to push your SSH key to all servers in your inventory:

```bash
ansible-playbook ansible-files/push-key.yml
```

Note: You may need to modify the playbook to use your specific user and SSH key path.

## Additional Playbooks

This repository also includes playbooks for:

- **Docker Installation**: `docker-files/docker-install.yml`
- **Docker Login**: `docker-files/docker-login.yml`
- **Vault Configuration**: `docker-files/vault.yml`
- **Git Installation**: `jenkins-files/git-install.yml`
- **Jenkins Installation**: `jenkins-files/jenkins-install.yml`

## Getting Started

1. Install Ansible using the provided script
2. Configure your inventory file at `/etc/ansible/hosts`
3. Run the desired playbooks for your infrastructure setup

## Requirements

- Ubuntu 24.04 LTS (Noble) or compatible system
- Root or sudo access
- Basic understanding of Ansible concepts