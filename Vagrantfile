# -*- mode: ruby -*-
# vi: set ft=ruby :

$time = Time.now.strftime("%Y%m%d_%H%M%S");
$boxname = "ubuntu/trusty64"
$vmname = "dev_base"
$virtname = $vmname + "_" + $time
$vb_cpus = 2
$vb_memory = 1024
$con_ip = "192.168.50.10"

Vagrant.configure(2) do |config|

  config.vm.box = $boxname
  config.vm.box_check_update = true
  config.vm.hostname = "frontend"
  config.vm.network "private_network", ip: $con_ip
  config.vm.synced_folder "./", "/vagrant/", create: true, owner: "vagrant", group: "vagrant"

  # config.vm.box_url = "http://example.com/box/box.json"
  # config.ssh.username = 'root'
  # config.ssh.password = 'vagrant'
  # config.ssh.insert_key = 'true'
  
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

