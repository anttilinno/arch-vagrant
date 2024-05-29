# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "archlinux/archlinux"
    config.vm.define "archlinux"
    config.vm.network "public_network"

    config.vm.disk :disk, size: "100GB", primary: true

    config.vm.provider "virtualbox" do |vb|
      vb.name = "Archlinux - Vagrant"
      vb.memory = "4096"
      vb.cpus = 4
      vb.gui = true
      vb.check_guest_additions = false
      vb.customize ['modifyvm', :id, '--accelerate3d', 'on']
      vb.customize ['modifyvm', :id, '--graphicscontroller', 'vmsvga']
      vb.customize ['modifyvm', :id, '--hwvirtex', 'on']
      vb.customize ['modifyvm', :id, '--ioapic', 'on']
      vb.customize ['modifyvm', :id, '--vram', '128']
      vb.customize ['modifyvm', :id, '--audio', 'none']
      vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']
      vb.customize ["modifyvm", :id, "--usb", "on"]
      vb.customize ["modifyvm", :id, "--usbehci", "on"]
    end

    $script = <<-SCRIPT
    sudo pacman -Sy
    sudo pacman -S archlinux-keyring --noconfirm
    sudo pacman -Su --noconfirm
    sudo pacman -S ansible git --noconfirm

    git clone https://github.com/anttilinno/blankarch.git
    SCRIPT

    config.vm.provision "shell", inline: $script, privileged: false
end
