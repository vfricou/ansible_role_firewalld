Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

`fwl_services`: Permit to define custom services will be included in Firewalld configuration
Example : 
```yaml
fwl_services:
  - name: 'test-service'
    description: 'Service long description'
    ports:
      - '8080'
      - '8443/tcp'
      - '9000/udp' 
```

`fwl_rules`: Permit to define rules will be included in Firewalld configuration.
Allow section will open specified.
Deny section will close specified.
Example :
```yaml
fwl_rules:
  allow:
    ports:
      - '443/tcp'
    sources:
      - '1.1.1.1'
    services:
      - 'ssh'
    rich_rules:
      - 'rule family="ipv4" source address="1.2.3.4/32" port port="8000" protocol="tcp" accept'
  deny:
    ports:
      - '80/tcp'
      - '443/tcp'
    sources:
      - '1.1.1.1'
    services:
      - 'cockpit'
    rich_rules:
      - 'rule family="ipv4" source address="1.2.3.4/32" port port="8000" protocol="tcp" accept'
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
