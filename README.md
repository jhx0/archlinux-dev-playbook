# archlinux-dev-playbook
A **Ansible** **Playbook** to deploy/configure a **ArchLinux** development system.   
The primary focus is a system running under **VirtualBox** - but you could certainly change that!

## Features:
- Installs a basic **Xfce** desktop (With Xfce4-Goodies)
- **LightDM** is used as a login manager
- **Development** related tools installed (**Go**, **MingW**, **GCC**, etc.)
- **VirtualBox** Guest Utilities installed/enabled
- Various **Sysctl** tweaks (Swappiness altered for example)
- **Dotfiles** already present
- **AUR** helper available: **Yay**
- **VSCodium** installed from the **AUR**

## Hint
This Playbook mainly servers my own needs - feel free to adapt it to yours!

You can find many more variables under the **vars** directory - Make sure you take a look before running the **Playbook**. (So you can customize your install)

The **dotfiles** tasks installs my own config files. This might not be what you need - be sure to exclude the **role** when not needed. (This can be done via **tags**)

## Before running the Playbook:
- Set the variables you need
- Take a look at the **dotfiles** role, since you most likely want to use your own dots!

## Usage:
1. Clone/download this repository
2. Unpack/cd into the directory
3. Run
```shell
$ ansible-playbook main.yml (-Kk)
```
4. The target will reboot when the playbook is finished running
5. Done

## Examples
All tasks can be selected via **Tags**, so you can pick whatever tasks you want to run.   
Following, a couple of use cases:
1. Run all tasks
```bash
$ ansible-playbook main.yml --tags all (-Kk)
```
2. Only run a subset of tasks
```bash
$ ansible-playbook main.yml --tags "pacman,upgrade,reboot" (-Kk)
```
3. Run only one task
```bash
$ ansible-playbook main.yml --tags "desktop" (-Kk)
```
All available **Tags**:
```bash
pacman
upgrade
dotfiles
sshd
sudo
groups
ntp
sysctl
grub
fail2ban
xorg
xfce
vbox
desktop
packages
development
fontconfig
yay
aur
reboot
```

## Note:
Make sure you have set the correct IP/Hostname in the **hosts** file.   

**BEWARE:** do **_NOT_** run this Playbook blindly!
