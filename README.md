# Ansible Playbook for provisioning `Vagrant` machines.

This is a general purpose ansible playbook to install essential packages for any web development project, to configure packages & setup proxy server (in environment variable, apt.conf, .gitconfig, /etc/environment etc) for accessing internet inside IIT Kharagpur.

The playbook has following roles:
### Roles
1. common
    - updates apt-cache
    - updates language
    - installs & ensures essential packages - build-essential, python-dev, vim, git, wget, curl
2. database
    - Installs & ensures mysql 
    - Installs & ensures mongodb
    - Installs & ensures postgresql
    - Creates database & User in postgresql with config in provisioning/roles/database/vars/main.yml
    - Changes user's db permissions
3. packages
    - Ensures nodejs & ruby
4. webserver
    - Ensures apache is running, loads config into sites-available, links symbolically to sites-enabled
    - Installs & ensures express
    - Ensures nginx is running, sets up reverse proxy & loads given nginx conf into sites-available directory
    - Installs php

### Pre-tasks
- sets up some environment variable 
- Updates apt-cache
- sets up proxy in /etc/environement (related to iitkgp)
- replaces original apt.conf file with my apt.conf
- copies my .gitconfig at ~/ in the machines.

The playbook uses [human_log.py](https://gist.github.com/dmsimard/cd706de198c85a8255f6) for pretty printing.

