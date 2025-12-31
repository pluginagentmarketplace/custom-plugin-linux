---
name: languages
description: "Linux programming languages - installation, configuration, development"
sasmp_version: "1.3.0"
bonded_agent: linux-expert
bond_type: PRIMARY_BOND
---

# Languages Skill

## Overview

Install and configure programming languages on Linux systems.

## Capabilities

- **Python**: pyenv, pip, virtualenv
- **Node.js**: nvm, npm, yarn
- **Go**: GOPATH, modules
- **Rust**: rustup, cargo
- **Java**: OpenJDK, Maven, Gradle

## Examples

```bash
# Install Python with pyenv
curl https://pyenv.run | bash
pyenv install 3.11.0
pyenv global 3.11.0

# Install Node.js with nvm
nvm install --lts
nvm use --lts
```

