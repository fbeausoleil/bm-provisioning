# bm-provisioning
Bare metal provisioning playground

## Structure

### roles/
Contains Ansible roles for bare metal server configuration:

- **Network Configuration**: Sets up dummy network interfaces (dm0) for anycast IP management
- **Ubuntu Support**: Configures netplan for Ubuntu systems
- **Service Management**: Creates systemd services for network interface management

#### Key Components
- `tasks/` - Ansible tasks for Ubuntu network configuration
- `handlers/` - Service restart handlers for systemd and netplan
- `templates/` - Jinja2 templates for netplan configuration
- `files/` - Static files including systemd service definitions
