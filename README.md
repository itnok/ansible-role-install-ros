install-ros-ubuntu
==================

[![Build Status](https://travis-ci.org/itnok/ansible-role-install-ros-ubuntu.svg?branch=master)](https://travis-ci.org/itnok/ansible-role-install-ros-ubuntu) [![GitHub tag](https://img.shields.io/github/v/tag/itnok/ansible-role-install-ros-ubuntu?sort=semver)](https://github.com/itnok/ansible-role-install-ros-ubuntu/tags/) [![Ansible Role](https://img.shields.io/ansible/role/47006)](https://galaxy.ansible.com/itnok/install_ros_ubuntu)

Install ROS on an Ubuntu host.

Steps performed are:

  - Using role [itnok.manage_pkg_ubuntu](https://galaxy.ansible.com/itnok/manage_pkg_ubuntu):
    * Make sure build_essentials package is installed
    * Add ROS repository key
    * Install choosen ROS metapackage & basic tools
  - Run `rosdep init` _(only if needed)_
  - Update ROS dependencies


## :exclamation: Requirements
-----------------------------

None.


## :abcd: Role Variables
------------------------

| Variable                | Description                                                             | Default Value       |
|-------------------------|-------------------------------------------------------------------------|---------------------|
| `install_ros_distro`    | Short name of the ROS distribution to install                           | `melodic`           |
| `install_ros`           | Name of the meta to install _(`ros-base`, `desktop`, `desktop-full`)_   | `ros-base`          |


## :link: Dependencies
----------------------

- [itnok.manage_pkg_ubuntu](https://galaxy.ansible.com/itnok/manage_pkg_ubuntu) _(:octocat: [ansible-role-manage-pkg-ubuntu](https://github.com/itnok/ansible-role-manage-pkg-ubuntu))_

To install dependencies use:
```
    $ ansible-galaxy install <dependecy.name>
```

Installation of the required Ansible Roles can also be simply addressed from they playbook using them with:
```
    $ ansible-galaxy install -r requirements.yml
```


## :notebook: Example Playbook
------------------------------

Here an example of how to use this role in your playbooks:

```
---
- hosts: servers
  remote_user: ubuntu   # optional (your remote user)
  gather_facts: yes     # optional
  become: yes

  roles:
    - { role: itnok.install_ros_ubuntu }

  vars:
    ros_install_distro: "melodic"
    ros_install_distro: "desktop-full"
```

## :guardsman: License
----------------------

MIT _([read more](LICENSE.md))_
