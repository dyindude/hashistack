dyindude.golang [![CircleCI](https://circleci.com/gh/dyindude/ansible-role-golang.svg?style=svg)](https://circleci.com/gh/dyindude/ansible-role-golang)
=========

Ansible role for installing and setting up a working golang distribution on a machine. Modeled after the official golang [docker images](https://hub.docker.com/_/golang/).

- The binary distribution gets installed to the default `$GOROOT`, `/usr/local/go`.
- `GOPATH` defaults to `/go` and can be changed via the default variable `golang_gopath`.
- `/etc/profile.d/gopath.sh` is rendered as a part of the installation and sets `GOPATH` and `PATH` appropriately (system-wide).

Role Variables
--------------
defaults:
```
golang_gopath: "/go"
golang_version: "1.11.2"
golang_arch: "linux-amd64"
```

Example Playbook
----------------

    - hosts: hosts
      roles:
         - dyindude.golang

License
-------

BSD

Author Information
------------------

dyindude
