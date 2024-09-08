# Ansible Scripts for Localhost Automation

## Overview

This repository contains a collection of Ansible playbooks and roles designed for automating tasks on a local machine (localhost). The scripts aim to simplify system administration, software installation, configuration management, and application deployment tasks. This setup is perfect for development, testing, or managing local environments.

## Repository Structure

```plaintext
.
├── playbooks/        # Contains Ansible playbooks
│   ├── installation-packages.yml    # Example playbooks
├── roles/            # Contains reusable Ansible roles
│   └── sample-role/  # Example role (tasks, handlers, files, templates)
├── group_vars/       # Group-specific variables
├── host_vars/        # Host-specific variables
├── inventory/        # Inventory files (e.g., localhost inventory)
│   └── hosts         # Inventory file defining localhost
└── README.md         # This README file
```

## Prerequisites

- **Ansible** version 2.9 or higher
- **Python** version 3.6 or higher
- A working **Git** installation
- Localhost configured with a supported OS (e.g., Linux, macOS, Windows Subsystem for Linux (WSL))

## Getting Started

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone <<URL>>
cd ansible-scripts
```

### 2. Install Ansible

If Ansible is not already installed, you can install it using the following commands:

#### For Debian/Ubuntu:

```bash
sudo apt update
sudo apt install ansible -y
```


### 3. Configure Inventory

Since you are targeting localhost, configure the `inventory/hosts` file:

```ini
[local]
localhost ansible_connection=local
```

### 4. Run a Playbook

To run a playbook on localhost, use the `ansible-playbook` command:

```bash
ansible-playbook -i inventory/hosts playbooks/installation-packages.yml
```

### 5. Example Playbooks

Here are some sample playbook structure:

#### 1. `sample-playbook.yml`

Installs a list of packages on localhost. You can customize the list of packages by editing the `vars` section in the playbook.

```yaml
---
- name: Install necessary packages
  hosts: local
  vars:
    packages:
      - git
      - curl
      - vim
  tasks:
    - name: Install packages
      apt:
        name: "{{ packages }}"
        state: present
      become: yes
```


### 6. Creating Ansible Roles

To create a new Ansible role, use the `ansible-galaxy` command:

```bash
ansible-galaxy init roles/your-role-name
```

This command will create a directory structure for your role under the `roles/` directory.

## Adding Variables

Use the `group_vars` and `host_vars` directories to manage variables for different groups or hosts:

- **`group_vars/`**: Contains variables for host groups.
- **`host_vars/`**: Contains variables for specific hosts.

## Troubleshooting

- **Ansible Command Not Found**: Ensure Ansible is installed and added to your system PATH.
- **Permission Denied Errors**: Use `become: yes` in playbooks to run tasks with elevated privileges (sudo).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For any questions or feedback, please connect with [Balachander T J on LinkedIn](https://www.linkedin.com/in/balachandertj).
