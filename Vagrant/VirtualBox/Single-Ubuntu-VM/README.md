# Homelab Vagrant VM with Docker

This repository contains a `Vagrantfile` for setting up a virtual machine (VM) with Docker, using Vagrant and VirtualBox. It's designed to quickly bootstrap a development environment for container-based applications.

## Prerequisites

Ensure you have the following tools installed on your host machine:

- [Vagrant](https://www.vagrantup.com/downloads.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

## VM Configuration

The VM is provisioned with the following configuration:

- **OS**: Ubuntu 18.04 LTS (Bionic Beaver)
- **Hostname**: `homelab.local`
- **Network**: Configured to use a public network
- **Storage**: 20GB virtual hard disk
- **RAM**: 1GB
- **CPU**: 1 core

Additionally, Docker and necessary Docker tools are installed to support containerization.

## Usage

To start using this Vagrant environment, follow these steps:

1. Clone this repository or download the `Vagrantfile`.
2. Open a terminal and navigate to the directory containing the `Vagrantfile`.
3. Execute the command `vagrant up` to create and provision the VM.

After the setup is complete, you can access the VM via SSH with the command `vagrant ssh`.

## Customization

If you require different configurations (e.g., more RAM or CPUs), you can edit the `Vagrantfile` before running `vagrant up`. Modify the values in the `vb.memory` and `vb.cpus` lines accordingly.

## Teardown

To halt the VM without destroying it, use `vagrant halt`. 

To completely remove the VM and all its components from your system, use `vagrant destroy`.

## Docker Usage

Once the VM is running, Docker is available for use. You can manage Docker containers directly within the VM using standard Docker commands.

## Networking

The VM is set up with a public network, meaning it can be accessed from the host machine's network. If you prefer to use a private network, you can change the `config.vm.network` line in the `Vagrantfile` to `private_network`.

## Shared Folder

The default shared folder is disabled in this setup. If you want to enable folder synchronization between your host and the VM, remove or comment out the `disabled: true` line or configure it according to your needs.

## License

The contents of this repository are covered under the MIT License.

---

Enjoy your Homelab environment!
