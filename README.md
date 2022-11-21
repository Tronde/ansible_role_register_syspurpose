register_syspurpose
===================

Register host to Red Hat Subscription Management (RHSM) and set System Purpose.

Requirements
------------

 * [community.general collection](https://galaxy.ansible.com/community/general)

You might already have installed this collection if you are using Ansible Engine 2.9 or the `ansible` package. It is not included in `ansible-core`. To check whether it is installed, run `ansible-galaxy collection list`.

To install it, use: `ansible-galaxy collection install community.general`.

To use it in a playbook, specify: `community.general.redhat_subscription`.

Role Variables
--------------

To set the variables for this role you need to know your RHSM ORG ID and an activation key. Please see the following URLs for more information on this:

 * [Understanding the Red Hat Subscription Management Organization ID](https://access.redhat.com/articles/3047431)
 * [Creating Red Hat Customer Portal Activation Keys](https://access.redhat.com/articles/1378093)

```yaml
register_syspurpose_activationkey: # activationkey for access.redhat.com or Satellite
register_syspurpose_password: # Org ID on access.redhat.com or Satellite
register_syspurpose_role: "Red Hat Enterprise Linux Server"
# possible values are:
# Red Hat Enterprise Linux Server
# Red Hat Enterprise Linux Workstation
# Red Hat Enterprise Linux Compute Node

register_syspurpose_sla: "Self-Support"
# possible values are:
# Premium
# Standard
# Self-Support

register_syspurpose_usage: "Development/Test"
# possible values are:
# Development/Test
# Disaster Recovery
# Production
```

I got these values from the KB [syspurpose_usage: "Development/Test"](https://access.redhat.com/articles/5713081).
There might be other possible values out there. In case you know some valid
addtional values please sent a PR to add them to this documentation.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

~~~
- hosts: all
  gather_facts: no
  vars:
    register_syspurpose_activationkey: rhel-dev-test
    register_syspurpose_password: 123456
  roles:
    - register_syspurpose
~~~

License
-------

MIT.

Author Information
------------------

Joerg Kastning - "joerg (dot) kastning '@' my-it-brain (dot) de"
