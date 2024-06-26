# Vagrant setup


## Install vagrant

* **Windows** Download [Vagrant](https://www.vagrantup.com/downloads) and install
* **Linux(Arch)** `pacman -S vagrant`

## Install vagrant plugins

```
vagrant plugin install virtualbox
```

## Run vagrant

If disk needs to be larger, than default size, set the ENV variable. Otherwise skip the environment variable.

```
# Set powershell env for experimental disks
$env:VAGRANT_EXPERIMENTAL="disks"
vagrant up
```

## Resize disks

If user needs bigger disk than 20GB

```
# delete and recreate partition
fdisk /dev/sda

reboot

# Resize btrfs filesystem
btrfs filesystem resize max /
```
## How to find network interface name in Windows

```
'C:\Program Files\Oracle\VirtualBox\VBoxManage.exe' list bridgedifs
```

## Run the playbook - [Inspiration](https://www.middlewareinventory.com/blog/run-ansible-playbook-locally/)

```
cd blankarch
ansible-playbook -i inventory.yml archlinux-playbook.yaml
```
