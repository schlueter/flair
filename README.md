# Flair
###### _For all your customization needs_
![Show some flair!](flair.jpg)
Let's all share our system customizations

## Usage

This is meant to be a shared set of scripts for all of the engineers at Refinery29 to customize our development machines, so usage should include–at least awareness of–contribution to this repo. That said, basic usage of this repo can be as simple as:
```
git clone git@github.com:refinery29/devops-homedirs.git
cd devops-homedirs
./tswift.yml --extra-vars dotfiles_user=tswift
```
This will execute the *tswift.yml* playbook according to its hash bang line. In this repo, each playbook will have a hash bang line which will use `ansible-playbook` with *vagrant.local.rf29.net* specified for the inventory.  with the extra variable `dotfiles_user` set to `tswift`.

## Playbooks
The playbooks are where the logic for setting up machines is directed. I use the word "directed" because most of the logic is contained in the roles. The simplest playbooks in this repo could just consist of list of `roles`, but most will include some variables–specified as `vars`–and perhaps some additional logic in the form of `tasks` or even `pre_tasks`.

For example, the tswift playbook:
```
#!/usr/bin/env ansible-playbook --inventory vagrant.local.rf29.net,
---
# Each member of this list is a *play*, thus this is a *playbook*
- hosts: all
  vars:
    dotfiles:
    - zshrc
    - gitconfig
    - vimrc
  pre_tasks:
  - name: Kisses 💋
    command: touch /var/💋
```

The hash bash line specifies use of ansible-playbook to execute this script with the inventory set to *vagrant.local.rf29.net* (the ',' is necessary as an inventory is usually more than one machine).
