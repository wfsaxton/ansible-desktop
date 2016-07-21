# Ansible for desktop

A simple and quick way to provision your development machine.

Tested on Ubuntu 16.01

## Features

- install favourites apps
- NTP and localization
- easy management of dotfiles (zsh, vim, ruby)

## Installation

```
sudo apt-get install git vim ansible
git clone ???
cd ansible-desktop
```

## Configure

edit `vars.yml`

```yaml
user: kris
```

## Usage

install everything:

    sudo ansible-playbook -v setup.yml

install certain tags:

    sudo ansible-playbook --tags zsh setup.yml

## Inspirations

* https://github.com/kalos/ansible-desktop

