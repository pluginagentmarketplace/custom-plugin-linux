---
name: development
description: "Linux development environment - compilers, build tools, IDEs"
sasmp_version: "1.3.0"
bonded_agent: linux-expert
bond_type: PRIMARY_BOND
---

# Development Skill

## Overview

Set up and optimize Linux development environments for various programming languages.

## Capabilities

- **Compilers**: GCC, Clang, rustc
- **Build Tools**: Make, CMake, Ninja
- **Version Control**: Git, SVN
- **IDEs**: VS Code, Vim, Emacs
- **Debugging**: GDB, Valgrind, strace

## Examples

```bash
# Install development tools
sudo apt install build-essential cmake git

# Compile C++ project
mkdir build && cd build
cmake .. && make -j$(nproc)
```

