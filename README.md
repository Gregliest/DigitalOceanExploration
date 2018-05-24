## Digital Ocean Exploration

A basic playbook for provisioning Digital Ocean Droplets.

## Using this repo

#### Create Droplet 
Create your droplet using the Digital Ocean [website](www.digitalocean.com) with the following options:
- Ubuntu 16.04.4
- Add ssh key that you have access to. 
- Keep the rest of the options as default.

#### Provision using the Ansible playbook
- Add your new Droplet's IP address to the `hosts` file (with the options specified in the comment)
- Change the path to your ssh key, if necessary in `Set up authorized keys for the user` in `automation.yaml`
- Run `ansible-playbook automation.yaml` from the root of this project

## What this repo does
- Creates a user, `scoopadmin` with sudo privileges
- Adds an ssh key for that user from the local machine
- Disables root login and password login
- Installs and starts Nginx and Fail2ban
- Sets up a firewall that only allows OpenSSH (port 22) and Nginx HTTP (port 80)
- Changes the html for the webpage

## Notes
- This playbook can only be run once, since it connect via root login ssh, and subsequently disables root login. Ideally, this playbook would be split in two, one to create the user and lock down root, and the other to make the rest of the changes. 
- An ssh key pair is included in the repo, _for demonstration purposes only_. Please don't use it for anything serious. 
