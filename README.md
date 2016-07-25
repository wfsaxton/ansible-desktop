# Ansible for desktop

A simple and quick way to provision your development machine.

Tested with:

* Ansible 2.1
* Ubuntu 16.01

## Features

- install favourites apps
- NTP and localization
- easy management of dotfiles (zsh, vim, ruby)

## Installation

### Ansible

Note: We use the Ansible PPA because the Ubuntu repository contains version
2.0.

```
sudo apt-get repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install git vim ansible
git clone ???
cd ansible-desktop
```

You can also install Ansible 2.1 from [source](http://docs.ansible.com/ansible/intro_installation.html).


## Configure

edit `vars.yml`

```yaml
user: kris
```

## Usage

install everything:

    ansible-playbook -K -v setup.yml

install certain tags:

    ansible-playbook -K --tags zsh setup.yml

`-K` will prompt for your root/sudo password if required.

## Private

Copy SSH private keys to `

Import GPG private keys:

```
gpg --allow-secret-key-import --import private.key
```

## Inspirations

* https://github.com/kalos/ansible-desktop

