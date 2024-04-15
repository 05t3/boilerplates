# Grafana on Vagrant

This repository provides a Vagrant setup for running Grafana in a Docker container on a VirtualBox VM. It is configured to be straightforward to set up and tear down, making it ideal for development and testing environments.

## Prerequisites

Before you start, you'll need to install the following software on your host machine:

- **Vagrant**: [Download Vagrant](https://www.vagrantup.com/downloads.html)
- **VirtualBox**: [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)

These tools are necessary to create and manage your virtual machine.

## Overview

The configuration includes the following:

- **VM Box**: Ubuntu 18.04 (hashicorp/bionic64)
- **Hostname**: grafana.local
- **Network**:
  - Public network configuration
  - Port 3000 forwarded from guest to host
- **Resources**:
  - 2GB of RAM
  - 1 CPU
  - 20GB of disk space
- **Provisioning**:
  - Docker and Docker Compose are installed.
  - Grafana is deployed using Docker Compose from a `docker-compose.yml` file present in the same directory as the `Vagrantfile`.

## Docker Compose Configuration

The `docker-compose.yml` file sets up Grafana with the following configuration:

```yaml
version: '3.8'
services:
  grafana:
    image: grafana/grafana-enterprise
    container_name: grafana
    restart: unless-stopped
    ports:
      - '3000:3000'
    volumes:
      - grafana-storage:/var/lib/grafana
volumes:
  grafana-storage: {}
```

This setup ensures that Grafana starts automatically with the VM and binds to port 3000, which is forwarded to the host. Data is persisted in a named volume grafana-storage.

## Getting Started

To get your Grafana VM up and running, follow these steps:

1. Clone this repository or download the `Vagrantfile` and `docker-compose.yml` to a local directory.
2. Open a terminal and change to the directory containing the `Vagrantfile`.
3. Run `vagrant up`. This command will start the VM, set up the network, and provision the Grafana service as specified.
4. Once the VM is running, Grafana will be accessible via http://localhost:3000.


## Using Grafana

After starting the VM, you can access Grafana through the web browser at http://localhost:3000. The default login credentials are usually `admin` for both username and password, unless specified differently in your Grafana setup.

## Modifying the Setup

- To change the forwarded port or any other network settings, edit the corresponding lines in the `Vagrantfile`.
- To increase the VM's resources, modify the `vb.memory` or `vb.cpus` values in the `Vagrantfile`.
- If you need to update the Grafana version or change its configuration, adjust your `docker-compose.yml` file located in the synced "/vagrant" directory on the VM.

## Shutting Down

- To stop the Grafana VM, you can run `vagrant halt`.
- If you want to completely remove the VM and all its related components from your system, run `vagrant destroy`.


## License

This project is open-sourced under the MIT license. Feel free to fork, modify, and use it as you see fit.