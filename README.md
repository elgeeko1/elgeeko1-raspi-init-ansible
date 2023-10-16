# Ansible role to provision a factory-fresh Raspberry Pi with Ubuntu image
This role is my personal playbook for configuring and maintaining
Raspberry Pis from a factory-fresh image. Creates a new user, sets the hostname
and configures SSH keys.

# Requirements
Provisioning host:
- ansible 2.15 or later

Target that will be configured:
- Ubuntu 22.04 or later

# How to use this role
```yaml
- name: factory-init
  hosts: all
  roles:
    - name: factory raspi init
      role: elgeeko1-raspi-init-ansible
```

Variables:
```yaml
# username to create for subsequent SSH access
raspi_user: raspi_user

# login password for raspi_user (override this!)
raspi_user_password: raspberry

# hostname for the rpi target
raspi_hostname: raspi
```

# How to install this role

### Install method 1: Install using ansible-galaxy

The most robust way to install this role is to use ansible-galaxy,
which is installed with ansible by default. ansible-galaxy is effectively a package manager for ansible. It installs roles
from the community, or from private git repos, into your local machine for use in your playbooks.

Start by adding this role to an ansible-galaxy dependency file. Typically this file lives alongside your playbook file and by convention is named `requirements.yml`.

Add the following section to `requirements.yml`:

```
roles:
  - name: elgeeko1-raspi-init-ansible
    src: https://github.com/elgeeko1/elgeeko1-raspi-init-ansible
    version: main
```

If there is already a `roles` section, simply append this role to
add it as a dependency.

Then, install the role using ansible-galaxy:

`ansible-galaxy install -r requirements.yml -v`

### Install method 2: Clone this repository into a `roles` directory

Use this method if you plan to modify this role, or if for some
reason the ansible-galaxy method fails.

Starting from your playbook directory, change into the `roles`
directory and clone:

```
$ ls
 > playbook.yml
 > roles/
$ cd roles/
roles$ git clone https://github.com/elgeeko1/elgeeko1-raspi-init-ansible
```
