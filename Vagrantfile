Vagrant.configure("2") do |config|

	name = 'ntravelc-box'

	config.vm.provider "virtualbox" do |v|
	  v.memory = 4096
	  v.cpus = 4
	end
    
    config.vm.define "ubuntu" do |ubuntu|
    
        ubuntu.vm.box = "trusty_daily"
        
        ubuntu.vm.network :forwarded_port, host: 8005, guest: 80 # Apache
        ubuntu.vm.network :forwarded_port, host: 9205, guest: 9200 # ElasticSearch
        ubuntu.vm.network :forwarded_port, host: 8085, guest: 81 # NGINX
        ubuntu.vm.network :forwarded_port, host: 5585, guest: 5432 # PostgreSQL
        ubuntu.vm.network :forwarded_port, host: 8585, guest: 8080 # PostgreSQL
    
        ubuntu.vm.provision "shell", path: "sh/base_setup.sh"
        ubuntu.vm.provision "shell", path: "sh/apache.sh"
        ubuntu.vm.provision "shell", path: "sh/postgresql_setup.sh"
        ubuntu.vm.provision "shell", path: "sh/geoserver.sh"
    end
    
    
end
