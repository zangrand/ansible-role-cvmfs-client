Indigo-dc.cvmfs-client
=========

Ansible role to install CernVM-FS Client.

Requirements
------------

Python is required on host to run ansible: sudo apt-get install python

The apt ansible module requires the following packages on host to run:

- python-apt (python 2)

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

Apache Licence v2

http://www.apache.org/licenses/LICENSE-2.0


Reference
---------

Official cvmfs documentation: http://cvmfs.readthedocs.io/en/stable/cpt-repo.html

NIKHEF documentation: https://wiki.nikhef.nl/grid/Adding_a_new_cvmfs_repository
~                                                                                           
