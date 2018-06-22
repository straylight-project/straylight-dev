# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "netbox-unified" do |netbox_unified|
        netbox_unified.vm.box = "ubuntu/bionic64"
        netbox_unified.vm.hostname = "netbox-unified"
        netbox_unified.vm.network "forwarded_port", guest: 80,  host: 20080, host_ip: "127.0.0.1"
        netbox_unified.vm.network "forwarded_port", guest: 80,  host: 20080, host_ip: "127.0.0.1"
        netbox_unified.vm.network "forwarded_port", guest: 443, host: 20443, host_ip: "127.0.0.1"
        netbox_unified.vm.provision "ansible" do |ansible|
            ansible.groups = {
              "netbox" => [ "netbox-unified" ]
            }
	    ansible.extra_vars = {
                ansible_python_interpreter: "/usr/bin/python3",
            }
            ansible.compatibility_mode = "2.0"
            ansible.playbook = "netbox_unified.yml"
        end
    end
end
