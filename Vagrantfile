# -*- mode: ruby -*-
# vi: set ft=ruby :


$desc = <<SCRIPT
echo    Yellotravel.com 
echo    Local Development Environment  
echo    'by skkim \<skkim@yellomobile.com\>'
echo  
echo    -    Done    -
echo 
echo 
SCRIPT


$time = Time.now.strftime("%Y%m%d_%H%M%S");
$boxname = "ubuntu/trusty64"
$vmname = "dev_base"
$virtname = $vmname + "_" + $time
$vb_cpus = 2
$vb_memory = 2048
$con_ip = "192.168.50.10"

Vagrant.configure(2) do |config|

  config.vm.box = $boxname
  config.vm.box_check_update = true
  config.vm.hostname = "frontend"
  # config.vm.box_url = "http://example.com/box/box.json"
  config.vm.network "private_network", ip: $con_ip, auto_config: false
  config.vm.synced_folder "./", "/vagrant/", create: true, owner: "vagrant", group: "vagrant"

  # config.ssh.username = 'root'
  # config.ssh.password = 'vagrant'
  # config.ssh.insert_key = 'true'

  config.vm.provision "shell", inline: $desc
  
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = $vb_memory
    vb.cpus = $vb_cpus
    vb.name = $virtname
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    # ansible.inventory_path = "provisioning/inventory"
    ansible.limit = "all"
  end


  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.synced_folder "src/", "~/dev_share/frontend", create: true, owner: "vagrant", group: "vagrant"
  # 
  
  # config.vm.box_check_update = false
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.network "public_network"
  # config.vm.synced_folder "../data", "/vagrant_data"
  
  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
  # 

end


msg_format = Vagrant::UI::Colored.new
msg_format.say(:warn, "\t===============================================")
msg_format.say(:warn, "\t| Vagrant setting ")
msg_format.say(:warn, "\t| IPaddr  ::  #$con_ip")
msg_format.say(:warn, "\t| BoxName ::  #$virtname")   
msg_format.say(:warn, "\t| CPU     ::  #$vb_cpus")   
msg_format.say(:warn, "\t| Memory  ::  #$vb_memory")      
msg_format.say(:warn, "\t===============================================")

def debug_log(msg, opt = {})
  level = opt[:level] || "ERROR"
  time  = opt[:time]  || Time.now
  puts "#{ time.ctime } [#{ level }] #{ msg }"
end

