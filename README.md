This is a [Vagrant](https://www.vagrantup.com) powered `Centos 7` VM (https://app.vagrantup.com/centos/boxes/7) provisioned with [Ansible](https://www.ansible.com), ready to work with the amazing and eclectic stuff from http://github.com/ferjgar.

It _should_ work out of the box on both Windows (tested on `Windows 10`) and macOS (tested on `macOS Sierra`) (and probably Linux!), but you know, shit happens.

# Requirements
- Vagrant (tested with `v1.9.8` on win, and `v1.9.8` on mac)
- VM provider (tested with VirtualBox `v5.0.14` on win and `v5.0.14` on mac)

# Synced folder
This depends on the chosen provider. The `Centos 7` box comes clean, so in order to be able to mount
the shared folder between host and guest, something needs to be installed.
