Vagrant.configure("2") do |config|
  config.vm.boot_timeout = 600

  # Definir la primera máquina virtual
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/bionic64"
    web1.vm.network "private_network", ip: "192.168.33.10"
    web1.vm.hostname = "web1"

    web1.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo ufw allow 'Apache'
      sudo systemctl enable apache2
    SHELL

    # Compartir carpeta local con directorio de Apache
    web1.vm.synced_folder "./html", "/var/www/html", SharedFoldersEnableSymlinksCreate: false
  end

  # Definir la segunda máquina virtual
  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/bionic64"
    web2.vm.network "private_network", ip: "192.168.33.11"
    web2.vm.hostname = "web2"

    web2.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo ufw allow 'Apache'
      sudo systemctl enable apache2
    SHELL

    # Compartir carpeta local con directorio de Apache
    web2.vm.synced_folder "./html", "/var/www/html", SharedFoldersEnableSymlinksCreate: false
  end
end
