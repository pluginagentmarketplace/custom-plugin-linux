---
name: scripting
description: "Linux shell scripting mastery - Bash, automation, cron jobs"
sasmp_version: "1.3.0"
bonded_agent: linux-expert
bond_type: PRIMARY_BOND
---

# Scripting Skill

## Overview

Advanced Linux shell scripting for automation and system administration.

## Capabilities

- **Bash Scripting**: Variables, loops, functions
- **Text Processing**: sed, awk, grep, cut
- **Automation**: cron, systemd timers
- **Error Handling**: Exit codes, traps
- **Best Practices**: Shellcheck, style guides

## Examples

```bash
#!/bin/bash
# Backup script
backup_dir="/backup/$(date +%Y%m%d)"
mkdir -p "$backup_dir"
tar -czf "$backup_dir/data.tar.gz" /var/data
```

