Role Name
=========

Ansible role to install CernVM FS client.

Requirements
------------

Pythonn is required on host to run ansible: sudo apt-get install python

The apt ansible module requires the following packages on host to run:

- python-apt (python 2)
- python3-apt (python 3)
- aptitude

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: server
      pre_tasks:
        - name: Get server public key
          get_url:
            url: 'https://raw.githubusercontent.com/mtangaro/galaxy-reference-data-repository/master/server_public_keys/elixir-italy.galaxy.refdata.pub'
            dest: '/tmp/'
      roles:
        - role: cvmfs-client
           server_url: '<IP ADDRESS OR URL STRATUM 0 OR STRATUM 1 SERVER>'
           repository_name: 'elixir-italy.galaxy.refdata'
           cvmfs_public_key_list_files: [ "/tmp/elixir-italy.galaxy.refdata.pub" ]
           proxy_url: '<PROXY SERVER OR DIRECT>'
           proxy_port: 80             


License
-------

Apache2
