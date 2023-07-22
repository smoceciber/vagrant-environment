Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/focal64"

N = 1

    if N == 1
        config.vm.define "master", primary: true do |master|
            master.vm.hostname = "master"
            master.vm.provider "virtualbox" do |vb|
                vb.name = "master"
                vb.memory = "4096"
                vb.cpus = 4
            end
            '''
            master.vm.provision "ansible" do |ansible|
                ansible.playbook = "playbooks/master-inventory.yml"
            end
            '''
        end
    else
        config.vm.define "master", primary: true do |master|
            master.vm.hostname = "master"
            master.vm.provider "virtualbox" do |vb|
                vb.name = "master"
                vb.memory = "4096"
                vb.cpus = 4
            end
            '''
            master.vm.provision "ansible" do |ansible|
                ansible.playbook = "playbooks/master-inventory.yml"
            end
            '''
        end
        (1..N).each do |i|
            config.vm.define "slave0#{i}" do |slave|
                slave.vm.hostname = "slave0#{i}"
                slave.vm.provider "virtualbox" do |vb|
                    vb.name = "slave0#{i}"
                    vb.memory = "2048"
                    vb.cpus = 2
                end
                '''
                if i == 1
                    slave.vm.provision "ansible" do |ansible|
                        ansible.playbook = "playbooks/backend-inventory.yml"
                    end
                end
                '''
            end
        end
    end
end