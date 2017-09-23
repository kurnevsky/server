# Install packages: pacman -S vagrant ebtables dnsmasq firewalld
# Optionally install package from aur: pacaur -S vagrant-libvirt
# Start daemons: systemctl start firewalld && systemctl start libvirtd
# Install vagrant-libvirt plugin: vagrant plugin install vagrant-libvirt
# Add your user to libvirt group: gpasswd -a user libvirt
# Run: vagrant up --provider=libvirt
# Credentials: vagrant:vagrant

Vagrant.configure(2) do |config|
  config.vm.provider "libvirt" do |libvirt|
    # libvirt.driver = "qemu"
    libvirt.driver = "kvm"
  end

  # Add possibility to use ~/.vagrant.d/insecure_private_key
  config.ssh.insert_key = false

  config.vm.define "server" do |srv|
    srv.vm.box = "archlinux/archlinux"
    srv.vm.box_check_update = true
    srv.vm.provider "libvirt" do |libvirt|
      libvirt.memory = 512
      libvirt.cpus = 2
    end
    srv.vm.hostname = "kurnevsky.net"
    srv.vm.network "private_network", ip: "192.168.99.48", :netmask => "255.255.255.0"
  end
end
