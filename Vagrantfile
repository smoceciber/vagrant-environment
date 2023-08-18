Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/focal64" # os definition

N = 2 # number of machines to create, one for master
S = N-1 # number of slaves

    if N == 1
        config.vm.define "master", primary: true do |master| # vm definition
            master.vm.hostname = "master" # hostname
            master.vm.provider "virtualbox" do |vb| # hypervisor definition
                vb.name = "master" # vm name
                vb.memory = "4096" # ammount of memory
                vb.cpus = 4 # number of cores
            end
        end
    else
        config.vm.define "master", primary: true do |master|
            master.vm.hostname = "master"
            master.vm.provider "virtualbox" do |vb|
                vb.name = "master"
                vb.memory = "4096"
                vb.cpus = 4
            end
        end
        (1..S).each do |i|
            config.vm.define "slave0#{i}" do |slave|
                slave.vm.hostname = "slave0#{i}"
                slave.vm.provider "virtualbox" do |vb|
                    vb.name = "slave0#{i}"
                    vb.memory = "2048"
                    vb.cpus = 2
                end
            end
        end
    end
end