# To support dual monitors (home instructions)

Copy the following to /home/wfsaxton/.config/monitors.xml

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DVI-I-1">
          <vendor>ACI</vendor>
          <product>0x24e1</product>
          <serial>0x01010101</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>2560</x>
          <y>213</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DP-1">
          <vendor>ACI</vendor>
          <product>0x27b1</product>
          <serial>0x000107b2</serial>
          <width>2560</width>
          <height>1440</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DP-2">
      </output>
      <output name="HDMI-1">
      </output>
      <output name="DP-3">
      </output>
  </configuration>
</monitors>
```

# To support external monitors

```
$ cvt 2560 1440 60
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
$ xrandr --newmode "2560x1440@60" 241,500 2560 2608 2640 2720 1440 1443 1448 1481 +hsync -vsync
$ xrandr --addmode DP1 "2560x1440@60"
```

# Ansible for desktop

A simple and quick way to provision your development machine.

Tested with:

* Ansible 2.3
* Mint 18.2

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
- Nunix Unity Theme
- Yunikey support
- Dotfiles
- Coding fonts
- Slack
- Sublimetext
- and more...

## Installation

Checkout the [Getting Started](https://github.com/krisleech/ansible-desktop/wiki/Getting-started) guide
for an overview and examples of the recipies used.

### Ansible

Note: We use the Ansible PPA because the Ubuntu repository contains the older
2.0 version.

```
sudo add-apt-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install git vim ansible
git clone git@github.com:krisleech/ansible-desktop.git
cd ansible-desktop
```

You can also install Ansible 2.1 from [source](http://docs.ansible.com/ansible/intro_installation.html).


## Configure

Edit `vars.yml` and change the `user` var:

```yaml
user: wfsaxton
```

## Usage

Install everything:

    ansible-playbook -K -v setup.yml

Install certain tags:

    ansible-playbook -K --tags zsh setup.yml

`-K` will prompt for your root/sudo password, if required.

## Notes

The numix theme is not enabled by default. To do so open the unity-tweak-tool
and select the theme.

There are several sessions which can be selected from the Greeter (login
screen) including Unity (Ubuntu default), Gnome, i3, and Gnome+i3.

I prefer Gnome+i3, this gives me a tiling window manager with all the
conveniences of the Gnome underpinnings.

## Vagrant/VirtualBox

```
vagrant up --provision
```

## Inspirations

* https://github.com/kalos/ansible-desktop
* https://github.com/chaosmail/dev-env
