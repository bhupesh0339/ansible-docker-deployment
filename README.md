## Running docker containers with ansible

This project demonstrates how to log in to a private DockerHub registry and install the required packages to run Docker containers. The code has been thoroughly tested on Ubuntu 22.04 but is compatible with any Ubuntu distribution version equal to or greater than 18.

## Prerequisites

Ensure the following prerequisites are met:

- System/Server with Ubuntu Operating System
- Ansible installed (version equal to or greater than 2.16.0)
- Docker login username and password
- If using a remote server, SSH private key and username are also required

##  Playbook Tasks Description

The project performs the following tasks in sequence:

1. Update apt repositories
2. Install all required packages
3. Login to Docker private registry
4. Allow port 443 in the server firewall for external communication
5. Run a Docker container named "nginx-example-docker" using the nginx:latest image and exposing it on port 443

## Getting Started

1. Clone this repository to your local machine.

```bash
git clone https://github.com/bhupesh0339/ansible-docker-deployment.git
```
Now switch directory

```bash
cd ansible-docker-deployment
```
### Before running the Ansible command, make the following changes to the hosts.ini file:

Replace **1.2.3.4** with your server's IP address. If testing locally, use localhost.<br />
Replace **ubuntu** with your server/system username.<br />
Replace **/path_and_name_of_your_ssh_private_key** with the path to your SSH private key.<br />


After making these modifications, run the following Ansible command:
```
ansible-playbook --ssh-extra-args='-o StrictHostKeyChecking=no' -i hosts.ini ansible-playbook.yml
```
Note: The --ssh-extra-args='-o StrictHostKeyChecking=no' flag is used to avoid SSH verification prompts and ensure a smoother execution. Be cautious when using this flag in a production environment

During execution, Ansible will prompt you for your Docker username and password. Enter these details, and Ansible will start configuring the server.






