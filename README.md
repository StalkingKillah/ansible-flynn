Flynn
=========

Flynn role for Ansible

Requirements
------------

Role requires this [filter](https://gist.github.com/StalkingKillah/b32c893ca12aa8bd8e3d) - [help](http://docs.ansible.com/developing_plugins.html#distributing-plugins)

The example playbook requires httplib2 on local machine (required by the uri module)

Role Variables
--------------

* discovery_token
* controller_domain
* default_route_domain

Example Playbook
----------------

	- hosts: 127.0.0.1
	  connection: local
	  tasks:
	    - name: be sure to get new discovery token
	      uri: url=https://discovery.etcd.io/new return_content=yes
	      register: discovery_token
	      tags: after-reboot
	    - set_fact: discovery_token={{discovery_token.content}}
	      tags: after-reboot
	- hosts: all
	  vars:
	    - domain: 'demo.localflynn.com'
	  tasks:
	    - { include: 'tasks/main.yml', discovery_token: "{{hostvars['127.0.0.1']['discovery_token']}}", controller_domain: "{{domain}}", default_route_domain: "{{domain}}" }
	  handlers:
	    - include: 'handlers/main.yml'

License
-------

BSD

Author Information
------------------

Djordje Stojanovic
