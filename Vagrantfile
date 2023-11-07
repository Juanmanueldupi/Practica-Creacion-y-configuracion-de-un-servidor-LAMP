Vagrant.configure("2") do |config|
    # Maquina Router
  config.vm.define :router do |router|
    router.vm.box = "debian/bookworm64"
    router.vm.hostname = "router"
    router.vm.synced_folder ".", "/vagrant", disabled: true
    # Agregar una interfaz de red publica
    router.vm.network :public_network,
        :dev => "br0",
        :mode => "bridge",
        :type => "bridge",
        use_dhcp_assigned_default_route: true
    # Agregar una interfaz de red privada
    router.vm.network :private_network,
       :libvirt__network_name => "red_intra",
       :libvirt__dhcp_enabled => false,
       :ip => "10.0.0.1",
       :libvirt__forward_mode => "veryisolated"
  end
  # Maquina Web
  config.vm.define :web do |web|
    web.vm.box = "debian/bookworm64"
    web.vm.hostname = "web"
    web.vm.synced_folder ".", "/vagrant", disabled: true
    # Agregar una interfaz de red privada
    web.vm.network :private_network,
       :libvirt__network_name => "red_intra",
       :libvirt__dhcp_enabled => false,
       :ip => "10.0.0.2",
       :libvirt__forward_mode => "veryisolated"
      # Agregar una interfaz de red privada
    web.vm.network :private_network,
       :libvirt__network_name => "red_datos",
       :libvirt__dhcp_enabled => false,
       :ip => "192.168.33.12",
       :libvirt__forward_mode => "veryisolated"
  end
# Maquina bd
  config.vm.define :bd do |bd|
    bd.vm.box = "debian/bookworm64"
    bd.vm.hostname = "bd"
    bd.vm.synced_folder ".", "/vagrant", disabled: true
    # Agregar una interfaz de red privada
    bd.vm.network :private_network,
       :libvirt__network_name => "red_intra",
       :libvirt__dhcp_enabled => false,
       :ip => "10.0.0.3",
       :libvirt__forward_mode => "veryisolated"
      # Agregar una interfaz de red privada
    bd.vm.network :private_network,
       :libvirt__network_name => "red_datos",
       :libvirt__dhcp_enabled => false,
       :ip => "192.168.33.14",
       :libvirt__forward_mode => "veryisolated"
  end
end
