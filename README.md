# Ansible Role: Nimbus Ethereum 2 Client

## Description

This Ansible role installs, configures, and manages **Nimbus**, an enterprise-grade Ethereum 2.0 client. Nimbus is designed for resource-efficient and secure operation on Ethereum's Beacon Chain and shard chains.

The role automates the full lifecycle of Nimbus, ensuring a reliable and reproducible setup for Ethereum 2.0 nodes.

---

## Features

- Installs Nimbus from source or prebuilt binaries  
- Configures Nimbus with customizable options  
- Sets up Nimbus as a system service (systemd) for automatic start and restart  
- Provides secure environment configuration and logging  
- Supports running Nimbus on multiple platforms supported by Ansible and Nimbus  

---

## Requirements

- Control node with Ansible 2.9+  
- Target hosts running a supported Linux distribution (e.g., Ubuntu, Debian, CentOS)  
- Internet access on target hosts for downloading dependencies and Nimbus binaries  

---

## Role Variables

| Variable           | Default       | Description                                  |
|--------------------|---------------|----------------------------------------------|
| `nimbus_version`   | `latest`      | Version of Nimbus to install (e.g., `v1.5.0`) |
| `nimbus_install_dir` | `/opt/nimbus` | Directory where Nimbus will be installed     |
| `nimbus_user`      | `nimbus`     | System user that runs Nimbus service          |
| `nimbus_service_name` | `nimbus`    | Name of the systemd service                    |
| `nimbus_config`    | `{}`          | Dictionary of Nimbus configuration parameters |

---

## Example Playbook

```yaml
- hosts: ethereum_nodes
  roles:
    - role: nimbus-ethereum2
      vars:
        nimbus_version: "v1.5.0"
        nimbus_install_dir: "/opt/nimbus"
        nimbus_user: "nimbus"
        nimbus_service_name: "nimbus"
        nimbus_config:
          network: "mainnet"
          data-dir: "/var/lib/nimbus"
          http-port: 5052
