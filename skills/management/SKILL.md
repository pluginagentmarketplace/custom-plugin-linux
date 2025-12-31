---
name: management
description: "Linux system management - packages, services, users"
sasmp_version: "1.3.0"
bonded_agent: linux-expert
bond_type: PRIMARY_BOND
---

# Management Skill

## Overview

Comprehensive Linux system management including packages, services, and user administration.

## Capabilities

- **Package Management**: apt, yum, dnf, pacman
- **Service Management**: systemd, init
- **User Management**: useradd, groups, sudo
- **Permissions**: chmod, chown, ACLs
- **Scheduling**: cron, at, systemd timers

## Examples

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Create new user
sudo useradd -m -s /bin/bash newuser
sudo passwd newuser
```

