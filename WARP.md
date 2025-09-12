# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a bare metal provisioning playground repository for experimenting with automated server deployment and configuration management.

## Development Environment

This repository uses Ansible for bare metal server configuration and network management.

### Common Commands

```bash
# Run ansible playbook against inventory
ansible-playbook -i inventory playbook.yml

# Check ansible syntax
ansible-playbook --syntax-check playbook.yml

# Run in check mode (dry run)
ansible-playbook -i inventory playbook.yml --check

# Run specific tags
ansible-playbook -i inventory playbook.yml --tags networking

# Test connectivity to hosts
ansible all -i inventory -m ping
```

### Git Workflow

```bash
# Check repository status
git status

# View recent changes
git --no-pager log --oneline -10

# View current changes
git --no-pager diff
```

## Architecture

This repository contains Ansible roles for bare metal server network configuration:

### roles/
- **Network Configuration**: Creates dummy network interfaces (dm0) for anycast IP management
- **Ubuntu Support**: Configures netplan for Ubuntu systems using Jinja2 templates
- **Service Management**: Manages systemd services for network interface lifecycle
- **Handler Integration**: Automatic service restarts and netplan application

### Key Files
- `roles/tasks/main.yaml` - Main task orchestration with Ubuntu detection
- `roles/tasks/ubuntu.yaml` - Ubuntu-specific network configuration tasks
- `roles/handlers/main.yaml` - Service restart and netplan handlers
- `roles/templates/netplan.yaml.j2` - Dynamic netplan configuration template
- `roles/files/create-dm0.service` - Systemd service for dummy interface creation

## Key Considerations

- **Ansible Idempotency**: All tasks use `when: not ansible_check_mode` to ensure safe execution
- **Ubuntu-Specific**: Current implementation targets Ubuntu systems with netplan
- **Dummy Interfaces**: Uses Linux dummy network interfaces for anycast IP configuration
- **Systemd Integration**: Leverages systemd for service lifecycle management
- **Template-Driven**: Network configuration uses Jinja2 templates with `anycast_ips` variable
- **Handler Automation**: Changes automatically trigger service restarts and netplan application

## Repository Status

Active development with Ansible roles for network configuration. The repository contains working roles for Ubuntu bare metal network setup with dummy interface management.
