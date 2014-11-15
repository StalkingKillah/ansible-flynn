ansible-flynn
=============

Flynn role for Ansible

# Variables
* discovery_token
* controller_domain
* default_route_domain

# Note
Playbook depends on httplib2 (for ansible uri module)

Role requires this [filter](https://gist.github.com/StalkingKillah/b32c893ca12aa8bd8e3d) - [help](http://docs.ansible.com/developing_plugins.html#distributing-plugins)