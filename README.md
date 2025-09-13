# bm-provisioning
Bare metal provisioning playground

An Ansible-based project for configuring dummy network interfaces on Ubuntu systems for anycast IP management.

## Usage

```bash
# Run the playbook locally
ansible-playbook playbook.yaml

# Run in check mode (dry run)
ansible-playbook playbook.yaml --check

# Run with specific tags
ansible-playbook playbook.yaml --tags networking
```

## Configuration

Edit `group_vars/all.yaml` to customize the anycast IP addresses:

```yaml
anycast_ips:
  - 192.168.100.1/32
  - 192.168.100.2/32
```

## Structure

### Core Files
- `playbook.yaml` - Main Ansible playbook for bare metal provisioning
- `group_vars/all.yaml` - Configuration variables including anycast IPs

### roles/networking/
Ansible role for network interface configuration:

- **Network Configuration**: Creates dummy network interfaces (dm0) for anycast IP management
- **Ubuntu Support**: Configures netplan for Ubuntu systems using Jinja2 templates
- **Service Management**: Manages systemd services for network interface lifecycle
- **Handler Integration**: Automatic service restarts and netplan application

#### Key Components
- `tasks/` - Ansible tasks for Ubuntu network configuration
- `handlers/` - Service restart handlers for systemd and netplan
- `templates/` - Jinja2 templates for netplan configuration
- `files/` - Static files including systemd service definitions
