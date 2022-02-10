Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian10"
  config.vm.hostname = "laravel"
  config.vm.provider "virtualbox" do |v|
    # v.gui = true
    v.name = "laravel"
    v.memory = 2048
    v.cpus = 1
    v.customize ['modifyvm', :id, '--clipboard', 'bidirectional']     
  end

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest:443, host: 8443
  config.vm.network "forwarded_port", guest: 22, host: 8022
  config.vm.netowrk "forwarded_port", guest: 3306, host: 8306
  
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update -y
    sudo apt-get upgrade -y
    sudo apt-get install -y net-tools
    sudo apt-get install -y openssh-server openssh-sftp-server
    sudo apt-get install -y openssl	
    sudo apt-get install -y apache2 apache2-doc
    sudo apt-get install -y mariadb-server mariadb-client
    sudo apt-get install -y php php7.3 libapache2-mod-php libapache2-mod-php7.3 php-mysql php7.3-mysql
    sudo apt-get install -y php-bcmath php-json php-mbstring php-tokenizer php-xml php-zip
    sudo apt-get install -y composer    
  SHELL

end
