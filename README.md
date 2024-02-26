# Vultr Ansible Playbook

![image](https://github.com/88plug/vultr-ansible-playbook/assets/19512127/1b8ed33b-25e1-495a-b6ba-cea896a1bafb)

This Ansible playbook automates the deployment and setup of Vultr VPS instances. It operates locally and executes commands remotely against newly created VPS instances.

## Prerequisites

Before running this playbook, ensure you have:

- **Vultr API Key**: Obtain from Vultr with appropriate permissions.
- **SSH Key Name**: Retrieve from Vultr CLI's `ssh-key list`.
- **Region**: Specify the deployment region.
- **Plan**: Choose the VPS plan from Vultr's offerings.
- **OS ID**: Identify the operating system ID.
- **Instance Count**: Determine the number of instances to deploy.
- **Label Base**: Set the base label for naming instances.

## Usage

1. **Clone Repository**:

    ```bash
    git clone https://github.com/88plug/vultr-ansible-playbook.git
    cd vultr-ansible-playbook
    ```

2. **Edit Configuration**:

    Modify variables in `deploy.yml` and `vps.yml` to fit your requirements. `deploy.yml` will create the new VPS on Vultr. `vps.yml` will configure the new VPS when SSH is ready. `vps.ini` will be created each time `deploy.yml` is run.

4. **Run Playbooks**:

    Execute the playbooks:

    ```bash
    ansible-playbook -i inventory.ini deploy.yml && ansible-playbook -i vps.ini vps.yml
    ```


## Playbook Overview

- **Ensure UTC Timezone**: Sets system timezone to UTC.
- **Deploy Vultr Instances**: Creates VPS instances on Vultr.
- **Sleep for Initialization**: Allows time for instance initialization.
- **List Vultr Instances**: Retrieves instance information.
- **Set Instance IPs**: Extracts IP addresses of deployed instances.
- **Display IPs**: Shows IP addresses of deployed instances.
- **Wait for SSH Access**: Waits until instances are SSH accessible.
- **Install Necessary Packages**: Installs required packages on instances.
- **Set GRUB Timeout**: Adjusts GRUB timeout for faster booting.
- **Disable UFW**: Turns off UFW (Uncomplicated Firewall) on instances.

## Note

Ensure your system meets all requirements and configurations specified in the playbook before execution.
