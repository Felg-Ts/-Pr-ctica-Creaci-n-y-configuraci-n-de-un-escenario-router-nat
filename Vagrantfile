Vagrant.configure("2") do |config|

  config.vm.define :nodo1 do |nodo1|
    nodo1.vm.box = "debian/bullseye64"
    nodo1.vm.hostname = "router"
    nodo1.vm.synced_folder ".", "/vagrant", disabled: true
    nodo1.vm.network :private_network,
      :libvirt__network_name => "redaislada",
      :libvirt__dhcp_enabled => false,
      :ip => "192.168.46.1",
      :libvirt__forward_mode => "veryisolated"
    nodo1.vm.network :public_network,
      :dev => "br0",
      :mode => "bridge",
      :type => "bridge",
      use_dhcp_assigned_default_route: true
    #nodo1.vm.provision "ansible" do |ansible|
      #ansible.playbook = "ansible/playbook.yml"
      #ansible.limit = "all:routers"
    #end
  end
  config.vm.define :nodo2 do |nodo2|
    nodo2.vm.box = "debian/bullseye64"
    nodo2.vm.hostname = "servidorweb"
    nodo2.vm.synced_folder ".", "/vagrant", disabled: true
    nodo2.vm.network :private_network,
      :libvirt__network_name => "redaislada",
      :libvirt__dhcp_enabled => false,
      :ip => "192.168.46.2",
      :libvirt__forward_mode => "veryisolated",
      use_dhcp_assigned_default_route: true
    #nodo2.vm.provision "ansible" do |ansible|
      #ansible.playbook = "ansible/playbook.yml"
      #ansible.limit = "all:servidores_web:clientes"
    #end
  end
end
