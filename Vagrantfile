Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network :forwarded_port, guest: 22, host: 2201, id: "ssh" #ssh
  config.vm.network :forwarded_port, guest: 80, host: 8001 #web
  config.vm.network :forwarded_port, guest: 3306, host: 33601 #mysql

  config.vm.synced_folder ".", "/var/www/html", type: "rsync",
    rsync__exclude: [".idea", ".git/", "vendor/", "app/config/parameters.yml", "app/cache", "app/logs", "web/.htaccess", "web/bundles", "web/css", "web/design", "web/extension", "web/js", "web/share", "web/var", "ide-twig.json"]

  config.vm.provision :shell, path: "bootstrap.sh"

  config.vm.hostname = "apiblog-practice"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = "2"
  end

  config.ssh.forward_agent = true
end
