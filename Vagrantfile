Vagrant.configure("2") do |config|
    # Selecciona la caja de Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # Configura la VM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configura la red para acceder al servidor web
    config.vm.network "private_network", type: "dhcp"
  
    # Comparte el directorio local con el directorio del servidor Apache
    config.vm.synced_folder "./html", "/var/www/html"
  
    # Provisiona el servidor Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      echo '<h1>Hola Mundo desde Apache y Vagrant</h1>' > /var/www/html/index.html
      sudo systemctl restart apache2
    SHELL
  end  