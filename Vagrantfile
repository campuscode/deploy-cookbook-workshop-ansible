# Vagrantfile
Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/bionic64'
  config.ssh.insert_key = false
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end

  config.vm.define "nginx" do |web|
    web.vm.hostname = "nginx.test"
    web.vm.provision :shell, inline: "fallocate -l 1G /swapfile && chmod 0600 /swapfile && mkswap /swapfile && swapon /swapfile && echo '/swapfile none swap sw 0 0' >> /etc/fstab"
    web.vm.network :private_network, ip: "192.168.60.6"
  end

  config.vm.define "web1" do |web|
    web.vm.hostname = "web1.test"
    web.vm.provision :shell, inline: "fallocate -l 1G /swapfile && chmod 0600 /swapfile && mkswap /swapfile && swapon /swapfile && echo '/swapfile none swap sw 0 0' >> /etc/fstab"
    web.vm.network :private_network, ip: "192.168.60.4"
  end

  config.vm.define "web2" do |web|
    web.vm.hostname = "web2.test"
    web.vm.provision :shell, inline: "fallocate -l 1G /swapfile && chmod 0600 /swapfile && mkswap /swapfile && swapon /swapfile && echo '/swapfile none swap sw 0 0' >> /etc/fstab"
    web.vm.network :private_network, ip: "192.168.60.5"
  end

  # Database server.
  config.vm.define "db" do |db|
    db.vm.hostname = "db.test"
    db.vm.provision :shell, inline: "fallocate -l 1G /swapfile && chmod 0600 /swapfile && mkswap /swapfile && swapon /swapfile && echo '/swapfile none swap sw 0 0' >> /etc/fstab"
    db.vm.network :private_network, ip: "192.168.60.7"
  end
end
