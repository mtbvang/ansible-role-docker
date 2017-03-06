[![Build Status](https://travis-ci.org/mongrelion/ansible-role-docker.svg?branch=master)](https://travis-ci.org/mongrelion/ansible-role-docker)

docker
=========

Install Docker

Requirements
------------

None

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------
Install Docker
```
- hosts: servers
  roles:
     - mongrelion.docker
```

Install latest docker on EL linux os family.
```
- hosts: servers
  roles:
     - mongrelion.docker
       docker_yum_state: latest
```

Install specific version of docker on EL linux os family. Note: yum does not downgrade correctly.
```
- hosts: servers
  roles:
     - mongrelion.docker
       docker_version_rhel: 1.13.1
```

Testing
-------
For development, we use Vagrant.
Bring the VM up with

```
$ vagrant up
```

This will automatically run the playbooks against the virtual machine once it's up.  
After making changes to any playbook, you can test the provisioning with

```
$ vagrant provision
```

License
-------

MIT

Author Information
------------------

You can find me on Twitter: [@mongrelion](https://twitter.com/mongrelion)
