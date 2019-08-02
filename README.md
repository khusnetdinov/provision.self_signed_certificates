# Provision.user
[![Galaxy](https://img.shields.io/badge/galaxy-provision.user-blue.svg?style=flat-square)](https://galaxy.ansible.com/khusnetdinov/provision.user/)

This receipt creates `user` for deployment and managing operations on Ubuntu server.

## What it does?

 Under root user it:
 
 * Creates user
 
 * Gets ssh key from local machine and puts to server user authorized_keys
 
 * Grant user sudo without password permissions
 
 * Restrict password login, allow only SSH connection
 
 * Restrict root login

## Files structure

```
├── /defaults/                  # Default variables for playbook
│   └── main.yml                # Variables for playbook
├── /meta/                      # Meta
│   └── main.yml                # Ansible Galaxy meta information
├── /tasks/                     # Play tasks
│   └── main.yml                # User provision task
│── README.md                   # Project description
│── hosts                       # Inventory file
└── playbook.yml                # Playbook file
```

## Usage

#### Set Variables

```yaml
  # defaults/main.yml

  # path for certificates
  provision_certificates_path: /etc/nginx/ssl
  # password for private key
  provision_certificate_passphrase: private_key_passphrase
  # domain name for generating certificates
  provision_certificate_domain: betterdocs.info
```

#### Set provision hosts

```ini
# hosts

[provision]

# Set you hosts
0.0.0.0
```

#### Run provision

```bash
$ ansible-playbook playbook.yml -i hosts -vvv
```
