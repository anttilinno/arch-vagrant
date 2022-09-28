# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.box = "archlinux/archlinux"
    config.vm.define "archlinux"
    config.vm.network "public_network", bridge: "Realtek USB GbE Family Controller"

    config.vm.disk :disk, size: "100GB", primary: true

    config.vm.provider "virtualbox" do |vb|
      vb.name = "VagrArch"
      vb.memory = "4096"
      vb.cpus = 4
      vb.gui = true
      vb.check_guest_additions = false
    end

    $script = <<-SCRIPT
    sudo pacman -Sy
    sudo pacman -Su --noconfirm
    sudo pacman -S ansible git --noconfirm
    ansible-galaxy collection install community.general
    SCRIPT

    config.vm.provision "shell", inline: $script, privileged: false
end
