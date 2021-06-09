Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "echo Hello"

  config.vm.define "splunk_master" do |splunk_master|
    splunk_master.vm.box = "centos/8"
      config.vm.network :forwarded_port, guest: 8000, host: 12345
      config.vm.network :forwarded_port, guest: 8089, host: 12346
      config.vm.host_name = 'splunkmaster'
      config.vm.provision "shell", path: "~/splunk_up.sh"
  end

  config.vm.define "ansible_master" do |ansible_master|
    ansible_master.vm.box = "centos/8"
      config.vm.network "private_network", ip: "10.0.0.200"
      config.vm.network :forwarded_port, guest: 22, host: 2223
      config.vm.host_name = 'ansiblemaster'
  end

 config.vm.define "client01" do |client01|
    client01.vm.box = "centos/8"
      config.vm.network "private_network", ip: "10.0.0.201"
      config.vm.network :forwarded_port, guest: 80, host: 11180
      config.vm.network :forwarded_port, guest: 22, host: 2224
      config.vm.host_name = 'client01'
  end

  config.vm.define "client02" do |client02|
    client02.vm.box = "centos/8"
      config.vm.network "private_network", ip: "10.0.0.202"
      config.vm.network :forwarded_port, guest: 80, host: 11181
      config.vm.network :forwarded_port, guest: 22, host: 2225
      config.vm.host_name = 'client02'
  end
end
