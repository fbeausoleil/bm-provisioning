# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a bare metal provisioning playground repository for experimenting with automated server deployment and configuration management.

## Development Environment

This is a new repository with minimal setup. The following commands and structure are anticipated based on typical bare metal provisioning projects:

### Common Commands

```bash
# Initialize and set up the development environment (when implemented)
make setup

# Run tests (when implemented)
make test

# Build deployment artifacts (when implemented)  
make build

# Deploy to test environment (when implemented)
make deploy-test

# Clean build artifacts (when implemented)
make clean
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

## Expected Architecture

Based on the project name, this repository likely will contain:

- **Infrastructure as Code**: Terraform, Ansible, or similar tools for server provisioning
- **Configuration Management**: Scripts and playbooks for automated server setup
- **Deployment Scripts**: Automation for deploying applications to bare metal
- **Monitoring/Observability**: Tools for tracking provisioned infrastructure
- **Testing Framework**: Integration tests for deployment workflows

## Key Considerations

- Bare metal provisioning typically involves network booting (PXE), DHCP configuration, and OS installation automation
- Infrastructure state management and idempotency are critical
- Security considerations for automated access to physical hardware
- Network configuration and VLAN management may be involved
- IPMI/BMC integration for hardware management

## Repository Status

This repository is currently in initial setup phase with only a README.md file. The codebase structure and tooling will emerge as development progresses.
