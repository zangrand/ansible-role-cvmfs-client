ctao.cvmfs_client
======================

Ansible role to install CernVM-FS Client with or w/o its containerd snapshotter

Requirements
------------

Python is required on host to run ansible.

Variables
---------

``repository_name``: set cvmfs server repository name (default: ``sw.cta-observatory.org``).

``cvmfs_server_url``: set cvmfs server complete url (default: ``http://grid-cvmfs-one.desy.de:8000/cvmfs/@fqrn@``).

``cvmfs_public_key_path``: set path for cvmfs keys (default: ``/etc/cvmfs/keys/{{ repository_name }}``).

``cvmfs_public_key``: set cvfms public key, usually `<repository_name.pub>` (default: ``{{ repository_name }}.pub``).

``cvmfs_preconfigured``: allow to mount cvmfs volumes importing preconfigured file: works for cern.ch and egi.eu repos (default: ``false``)

``proxy_url``: set proxy name (default: ``DIRECT``).

``proxy_port``: set proxy port (default: ``80``).

``cvmfs_http_proxy``: set proxy complete url (default: ``http://{{ proxy_url }}:{{ proxy_port }}``).

``cvmfs_mountpoint``: set cvmfs mount point (default: ``/cvmfs``). If set to ``/cvmfs`` the role will use ``cvmfs_config probe`` to mount the repository.

``add_fstab_entry``: add fstab entry to automatically mount the repository (default: ``true``).

``snapshotter``: install and configure the cvmfs-snapshotter (default: ``false``).

``snapshotter_path``: path where to install the cvmfs-snapshotter software (default: ``/usr/local/share``).

Example Playbook
----------------

The role configures the CTAO cvmfs repository

```yaml
  - hosts: localhost
    roles:
      - role: ctao.cvmfs_client
        cvmfs_server_url: 'http://grid-cvmfs-one.desy.de:8000/cvmfs/@fqrn@'
        repository_name: 'sw.cta-observatory.org'
        cvmfs_public_key_path: '/etc/cvmfs/keys/sw.cta-observatory.org'
        cvmfs_http_proxy: "'http://squid-01.pd.infn.it:3128|http://squid-02.pd.infn.it:3128'"
        proxy_url: 'squid'
        snapshotter: false
```


License
-------

Apache Licence v2: http://www.apache.org/licenses/LICENSE-2.0

Reference
---------

Official cvmfs documentation: http://cvmfs.readthedocs.io/en/stable/cpt-repo.html

NIKHEF documentation: https://wiki.nikhef.nl/grid/Adding_a_new_cvmfs_repository
