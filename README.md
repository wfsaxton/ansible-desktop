# Ansible for desktop

A simple and quick way to provision your development machine.

Tested with:

* Ansible 2.1
* Ubuntu 16.01

## Features

- Zsh, NeoVIM, Tmux
- Chrome, Firefox
- PGP, Tor, Password Manager
- NTP and localization
- Ruby, Java, Clojure
- Redis, ES, MySQL
- Vritualbox, Vagrant
- Dropbox
- Rocketchat, Skype, Slack
- i3 Window Manager
- Dotfiles

## Installation

Note: Before going any further it is recommended to fork this repository so that you
can make changes and commit them back to your own repo.

### Ansible

Note: We use the Ansible PPA because the Ubuntu repository contains the older
2.0 version.

```
sudo apt-get repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install git vim ansible
git clone git@github.com:krisleech/ansible-desktop.git
cd ansible-desktop
```

You can also install Ansible 2.1 from [source](http://docs.ansible.com/ansible/intro_installation.html).


## Configure

Edit `vars.yml` and change the `user` var:

```yaml
user: kris
```

## Usage

Install everything:

    ansible-playbook -K -v setup.yml

Install certain tags:

    ansible-playbook -K --tags zsh setup.yml

`-K` will prompt for your root/sudo password, if required.

## Private

Copy SSH private keys to `~/.ssh`.

Import GPG private keys:

```
gpg --allow-secret-key-import --import /media/USBPEN/private.key
```

## Inspirations

* https://github.com/kalos/ansible-desktop
* https://github.com/chaosmail/dev-env
