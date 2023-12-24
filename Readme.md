# Ansible role [influxdb-1](https://galaxy.ansible.com/ui/standalone/roles/buluma/influxdb-1/documentation)

Install and configure InfluxDB.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-influxdb-1/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-influxdb-1/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-influxdb-1.svg)](https://github.com/buluma/ansible-role-influxdb-1/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-influxdb-1.svg)](https://github.com/buluma/ansible-role-influxdb-1/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-influxdb-1.svg)](https://github.com/buluma/ansible-role-influxdb-1/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/influxdb-1)](https://galaxy.ansible.com/ui/standalone/roles/buluma/influxdb-1/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-influxdb-1/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  roles:
    - role: boutetnico.influxdb

      influxdb_orgs:
        - name: main-org
          description: Main organization
        - name: guest-org

      influxdb_users:
        - name: admin01
          org: main-org
          password: secretPassword
        - name: guest01
          org: guest-org
          password: secretPassword

      influxdb_buckets:
        - name: bucket01
          description: First bucket
          org: main-org
          retention: 1d
        - name: bucket02
          org: main-org
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-influxdb-1/blob/master/defaults/main.yml):

```yaml
---
influxdb_dependencies:
  - apt-transport-https
  - curl
  - gnupg

influxdb_packages:
  - influxdb2
  - influxdb2-cli

influxdb_package_state: present

influxdb_config_path: /etc/influxdb
influxdb_bolt_path: /var/lib/influxdb/influxd.bolt
influxdb_engine_path: /var/lib/influxdb/engine

influxdb_host: http://localhost:8086

influxdb_config: {}
#  http-bind-address: 0.0.0.0:8086
#  reporting-disabled: true

influxdb_primary_org: example-org
influxdb_primary_bucket: example-bucket
influxdb_primary_username: example-user
influxdb_primary_password: ExAmPl3PA55W0rD

# Set your root token for admin user
influxdb_admin_token: EXAMPLE-TOKEN

influxdb_orgs: []
#  - name: main-org
#    description: Main organization
#  - name: guest-org

influxdb_users: []
#  - name: admin01
#    org: main-org
#    password: secretPassword
#  - name: guest01
#    org: guest-org
#    password: secretPassword

influxdb_buckets: []
#  - name: bucket01
#    description: First bucket
#    org: main-org
#    retention: 1d
#  - name: bucket02
#    description: Second bucket
#    org: main-org

influxdb_service_enabled: true

influxdb_service_state: started
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-influxdb-1/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-influxdb-1/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|bionic, focal|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|bullseye, buster|

The minimum version of Ansible required is 2.7, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-influxdb-1/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-influxdb-1/blob/master/CHANGELOG.md)

## [License](#license)

[MIT](https://github.com/buluma/ansible-role-influxdb-1/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)


Template inspired by [Robert de Bock](https://github.com/robertdebock)
