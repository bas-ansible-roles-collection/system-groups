
# System Groups (system-groups)

Master: [![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/system-groups/branches/master/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/system-groups)
Develop: [![Build Status](https://semaphoreci.com/api/v1/bas-ansible-roles-collection/system-groups/branches/develop/badge.svg)](https://semaphoreci.com/bas-ansible-roles-collection/system-groups)

Creates one or more operating system user groups with various optional attributes.

**Part of the BAS Ansible Role Collection (BARC)**

**This role uses version 0.3.1 of the BARC flavour of the BAS Base Project - Pristine**.

## Overview

* Creates, or removes, one or more operating system user groups
* Optionally, sets a number of group attributes such as GID and whether a group is a system group

## Quality Assurance

This role uses manual and automated testing to ensure its features work as advertised.
See [here](tests/README.md) for more information.

## Ansible compatibility

* this role supports Ansible 1.8 or higher in the 1.x series
* this role supports Ansible 2.x

**Note:** Support for Ansible 1.x is deprecated by this role, future versions will support Ansible 2.x only.

More information on Ansible compatibility is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Ansible-compatbility).

## Dependencies

* None

More information on role dependencies is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-dependencies)

## Requirements

* None

More information on role requirements is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-requirements)

## Limitations

* None

More information on role limitations is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-limitations)

## Usage

### BARC Manifest

By default, BARC roles will record that they have been applied to a system, this is termed the BAS Manifest.
The specific local facts set for this role are:

* `ansible_local.barc_system_groups.general.role_applied` - (boolean) records whether a role has been applied
* `ansible_local.barc_system_groups.general.role_version` - (string) records the version of the role that was applied

Note: You **SHOULD** use this feature to determine whether this role has been applied to a system.
If you do not want these facts to be set by this role, you **MUST** skip the **BARC_SET_MANIFEST** tag.

More information is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Role-Manifest)

### Typical playbook

```yaml
---

- name: ...
  hosts: all
  become: yes
  vars:
    system_groups_groups:
        -
          name: project-x
  roles:
    - bas-ansible-roles-collection.system-groups
```

### Tags

BARC roles use standardised tags to control which aspects of an environment are changed by roles.
Tasks in this role will 'tag' themselves with these tags as appropriate, typically in `tasks/main.yml`.

More information is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Appendix-B---BARC-Standardised)

### Variables

#### *system_groups_barc_role_name*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: `system_groups`

#### *system_groups_barc_role_version*

* **MUST NOT** be specified
* Specifies the name of this role within the BAS Ansible Roles Collection (BARC) used for setting local facts
* See the *BARC roles manifest* section for more information
* Example: `2.0.0`

#### *system_groups_groups*

A list of operating system user groups, and their properties, to be managed by this role.

* **MAY** be specified

Structured as a list of items, with each item having the following properties:

* *name*
  * **MUST** be specified
  * Values **MUST** be valid group names, as determined by the operating system
  * Example: `project-x`
* *gid*
  * **MAY** be specified
  * Specifies whether the user should have a fixed GID, or if should be allocated by the operating system
  * Values **MUST** be valid group GIDs, as determined by the operating system
  * Values **SHOULD** respect operating system conventions for system/non-system groups and reserved or special ranges
  * Where not specified, the operating system will assign a suitable GID (i.e. the next in the relevant range)
  * Specifying this property is non-default behaviour
  * Example: `1001`
* *system*
  * **MAY** be specified
  * Specifies whether a group is considered a 'system' group or a 'user' group
  * Operating system conventions for system/non-system groups **SHOULD** be respected
  * Values **MUST** use one of these options, as determined by Ansible:
    * `yes`
    * `no`
  * Specifying this property is non-default behaviour
  * Example: `yes`
* *state*
  * **SHOULD** be specified
  * Specifies whether the group should be present, or absent
  * Values **MUST** use one of these options, as determined by Ansible:
    * `present`
    * `absent`
  * Where not specified it will be assumed the group should be present
  * Example: `present`

Default: `[]` - an empty list

## Developing

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the
[BAS Ansible Roles Collection](https://jira.ceh.ac.uk/projects/BARC) (BARC) project on Jira.

This service is currently only available to BAS or NERC staff, although external collaborators can be added on request.
See our contributing policy for more information.

More information is also available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Issue-Tracking)

### Source code

All changes should be committed, via pull request, to the canonical repository:

`ssh://git@stash.ceh.ac.uk:7999/barc/system-groups.git`

A read-only mirror of this repository is maintained on GitHub:

`git@github.com:bas-ansible-roles-collection/system-groups.git`

More information is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Source-Code)

### Contributing policy

This project welcomes contributions, see `CONTRIBUTING.md` for our general policy.

### Release procedure

The general release procedure for BARC roles is available in the
[BARC General Documentation](https://antarctica.hackpad.com/BARC-Overview-and-Policies-SzcHzHvitkt#:h=Release-procedures)

## Licence

Copyright 2016 NERC BAS.

Unless stated otherwise, all documentation is licensed under the Open Government License - version 3.
All code is licensed under the MIT license.

Copies of these licenses are included within this project.
