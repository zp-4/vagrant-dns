Vagrant.configure("2") do |config|

  config.vm.define "dns" do |cfg|
    cfg.vm.box = "bento/ubuntu-22.04"
    cfg.vm.hostname = "ns1"
    cfg.vm.provision :shell, path: "dns_bootstrap.sh"
    cfg.vm.network :private_network, ip: "192.168.56.199", gateway: "192.168.56.1"
    cfg.vm.disk :disk, size: "5GB", primary: true

    cfg.vm.provider "virtualbox" do |vb, override|
      vb.gui = true
      vb.name = "P-DNS"
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 1]
      vb.customize ["modifyvm", :id, "--vram", "32"]
#      vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
#      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
  end
end


