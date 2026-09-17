# Ubuntu Dev Environment with Vagrant

A lightweight Ubuntu 24.04 development environment provisioned automatically with Vagrant and VirtualBox.

This project provides a reusable base virtual machine with common development, networking, and system administration tools pre-installed, so they do not need to be installed manually every time the virtual machine is created.

## Prerequisites

Before using this project, make sure the following are installed on your host system:

- [Vagrant](https://developer.hashicorp.com/vagrant)
- [VirtualBox](https://www.virtualbox.org/)

You can verify the installations with:

```bash
vagrant --version
VBoxManage --version
```

## Installation

Clone the repository:

```bash
git clone https://github.com/itspinkypenguin/vagrant-ubuntu-dev.git
```

Enter the project directory:

```bash
cd ubuntu-dev
```

Start and provision the virtual machine:

```bash
vagrant up
```

Vagrant will automatically:

1. Download the Ubuntu 24.04 base box if it is not already available.
2. Create the virtual machine using VirtualBox.
3. Configure the VM resources.
4. Set the hostname to `ubuntu-dev`.
5. Install the required packages.
6. Enable and start Nginx.

## Access the Virtual Machine

Connect to the VM using:

```bash
vagrant ssh
```

After connecting, you can verify the environment:

```bash
hostname
python3 --version
git --version
nginx -v
```

## Installed Tools

The VM includes the following base tools:

### Development

- Git
- Build Essential
- Python 3
- pip
- Python venv

### Networking & System Utilities

- curl
- wget
- iproute2
- dnsutils
- net-tools
- jq
- htop
- tree

### Editors & File Utilities

- Vim
- Nano
- zip
- unzip

### Package & Repository Utilities

- ca-certificates
- gnupg
- lsb-release
- software-properties-common

### Web Server

- Nginx

Nginx is enabled and started automatically during provisioning.

## Virtual Machine Configuration

| Setting   | Value        |
|-----------|--------------|
| OS        | Ubuntu 24.04 |
| Provider  | VirtualBox   |
| Hostname  | `ubuntu-dev` |
| Memory    | 4096 MB      |
| CPUs      | 4            |

## Common Vagrant Commands

Start the VM:

```bash
vagrant up
```

Connect to the VM:

```bash
vagrant ssh
```

Stop the VM:

```bash
vagrant halt
```

Restart the VM:

```bash
vagrant reload
```

Run provisioning again:

```bash
vagrant provision
```

Check the VM status:

```bash
vagrant status
```

Destroy the VM:

```bash
vagrant destroy
```

## Nginx

Nginx is installed, enabled, and started automatically during provisioning.

Check its status:

```bash
systemctl status nginx
```

Test the service:

```bash
curl http://localhost
```

You can also check whether Nginx is listening:

```bash
ss -tulpn | grep nginx
```

## Project Structure

```text
.
├── Vagrantfile
├── README.md
└── .gitignore
```

The `Vagrantfile` contains both the virtual machine configuration and the provisioning instructions.

## Purpose

This project is intended to provide a reusable Ubuntu base environment for development and DevOps practice.

The environment intentionally includes only common and frequently used tools. Larger technologies such as Docker, Kubernetes, Terraform, Ansible, Node.js, Go, and Java are not included so that the base environment remains lightweight and focused.

Additional tools can be installed separately depending on the requirements of each project.

## License

This project is provided for educational and personal use.
