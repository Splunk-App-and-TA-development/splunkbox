# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # search head
    config.vm.define "head", primary: true do |head|
        head.vm.box = "centos7"

        # provision with ansible
        head.vm.provision "ansible" do |ansible|
            ansible.playbook = "site.yml"
            ansible.skip_tags = 'splunk'
            ansible.host_key_checking = false
        end
    end
    # forwarder1
    config.vm.define "fwd1" do |fwd1|
        fwd1.vm.box = "centos7"

        # provision with ansible
        fwd1.vm.provision "ansible" do |ansible|
            ansible.groups = {
              "forwarders" => ["fwd1"],
            }
            ansible.playbook = "site.yml"
            ansible.skip_tags = 'splunk'
            ansible.host_key_checking = false
        end
    end
    # forwarder2
    config.vm.define "fwd2" do |fwd2|
        fwd2.vm.box = "centos7"

        # provision with ansible
        fwd2.vm.provision "ansible" do |ansible|
            ansible.groups = {
              "forwarders" => ["fwd1", "fwd2"],
            }
            ansible.playbook = "site.yml"
            ansible.skip_tags = 'splunk'
            ansible.host_key_checking = false
        end
    end
end
