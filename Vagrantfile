Vagrant.configure("2") do |config|
    # Configuración de la VM
    config.vm.box = "ubuntu/bionic64"  # Usa la imagen de Ubuntu 18.04 (Bionic)
    config.vm.network "forwarded_port", guest: 80, host: 8080  # Redirecciona el puerto 80 de Apache al 8080 local
  
    # Asigna memoria y CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configuración del servidor Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      echo "Hola Mundo desde Apache en Vagrant!" | sudo tee /var/www/html/index.html
    SHELL
  
    # Comparte la carpeta local con el servidor web
    config.vm.synced_folder ".", "/var/www/html"
  end