# sentry-self-hosted-ansible

This is an experiment to see how far i can go with ansible and how much effort it is to convert the bash centric repo of Sentry.

## Prerequisites

* Ansible 6
* Docker 20.10.21
* Time

Things might work with older versions, i haven't tested those, and frankly i'm not going to.

## Installation

```bash
ansible-galaxy install -r requirements.yml --force
```

## Testing

### Setup prerequisites

```sh
python3 -m pip install molecule ansible-core
python3 -m pip install --user "molecule[docker]"
python3 -m pip install --user "molecule[podman]"
```

### Add podman registry
```
[registries.search]
registries = ['docker.io']
```
### Initialize Docker containers for testing

```sh
molecule create
```

### Test

Default test ( runs in github actions)
```sh
cd playbook
molecule test
```

Local tests using podman, because there's some issues with docker i can't seem to figure out
```sh
cd playbook
molecule test --scenario-name local
```
