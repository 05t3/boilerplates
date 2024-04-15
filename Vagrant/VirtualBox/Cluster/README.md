# Node Cluster Setup with Vagrant

This repository contains a `Vagrantfile` for setting up a small cluster of virtual machines (VMs) using Vagrant. This setup is ideal for development, testing, and homelab experiments.

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- [Vagrant](https://www.vagrantup.com/downloads.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

These software pieces are required to create and manage the virtual machines.

## Configuration

The `Vagrantfile` is configured to set up 3 VMs (named `node-01`, `node-02`, and `node-03`). Each VM is provisioned with the following specifications:

- **OS**: Ubuntu 18.04 LTS (Bionic Beaver)
- **Hostname**: `node-01.local`, `node-02.local`, `node-03.local`
- **Network**: Configured to use a public network
- **Storage**: 20GB VMDK
- **RAM**: 1GB
- **CPUs**: 1

Docker and its associated packages are installed on each VM for containerization purposes.

## Getting Started

To get the cluster running, follow these steps:

1. Clone this repository or copy the `Vagrantfile` to a local directory.
2. Open a terminal and navigate to the directory containing the `Vagrantfile`.
3. Run the command `vagrant up` to start and provision all three VMs.
4. If you prefer to start a specific VM, run `vagrant up node-01` (replace `node-01` with the desired VM name).

Once the VMs are up and running, you can access each one via SSH using the command `vagrant ssh node-01` (_replace `node-01` with the desired VM name_).

## Customization

If you need to customize the VMs, you can edit the `Vagrantfile`. For example, you may want to change the number of VMs, adjust the hardware specifications, or modify the provisioning script.

## Teardown

To stop the VMs, use the command `vagrant halt`. 

If you wish to destroy the VMs and remove all traces from your system, use `vagrant destroy`.

## Notes

- The Docker installation steps in the provisioning script are designed for Ubuntu 18.04 LTS. If you use a different base box, the installation commands may differ.
- The public network configuration will allow the VMs to be accessible from your local network. Ensure your firewall settings allow for this, or modify the `Vagrantfile` to use a private network if necessary.

## License

This `Vagrantfile` and associated scripts are provided under the MIT License. Feel free to use and modify them as you see fit.

---