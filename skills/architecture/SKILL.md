---
name: architecture
description: "Linux system architecture - processes, memory, storage, kernel"
sasmp_version: "1.3.0"
bonded_agent: linux-expert
bond_type: PRIMARY_BOND
---

# Architecture Skill

## Overview

Understanding Linux system architecture including processes, memory, and kernel internals.

## Capabilities

- **Processes**: fork, exec, signals
- **Memory**: Virtual memory, paging, swap
- **Storage**: Block devices, filesystems
- **Kernel**: Modules, syscalls, interrupts
- **Boot**: GRUB, initramfs, systemd

## Examples

```bash
# View process tree
pstree -p

# Check memory usage
free -h
cat /proc/meminfo

# List kernel modules
lsmod
```

