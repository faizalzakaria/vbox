
Vagrant::Config.run do |config|

  config.vm.define :ubuntu do |ubuntu_config|
    ubuntu_config.vm.box = "ubuntu"
    ubuntu_config.vm.box_url = "http://cloud-images.ubuntu.com/precise/current/precise-server-cloudimg-vagrant-amd64-disk1.box"
		# ubuntu_config.vm.boot_mode = :gui
		ubuntu_config.vm.network :hostonly, "192.168.33.10"

		# Forward a port from the guest to the host, which allows for outside
		# computers to access the VM, whereas host only networking does not.
		ubuntu_config.vm.forward_port 80, 8080
		ubuntu_config.vm.forward_port 22, 2222
		ubuntu_config.ssh.forward_agent = true

		ubuntu_config.vm.share_folder("v-root", "/vagrant", ".", :nfs => true)

		ubuntu_config.vm.customize ["modifyvm", :id, "--memory", 1024]

		ubuntu_config.vm.provision :puppet, :options => "--verbose --debug" do |puppet|
			puppet.module_path = ""
		end

	end

  config.vm.define :fedora do |fedora_config|
    fedora_config.vm.box = "fedora"
    fedora_config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/fedora-18-x64-vbox4210.box"
		# fedora_config.vm.boot_mode = :gui
		fedora_config.vm.network :hostonly, "192.168.33.10"

		# Forward a port from the guest to the host, which allows for outside
		# computers to access the VM, whereas host only networking does not.
		fedora_config.vm.forward_port 80, 8080
		fedora_config.vm.forward_port 22, 2222
		fedora_config.ssh.forward_agent = true

        fedora_config.vm.share_folder("v-root", "/vagrant", ".", :nfs => true)

		fedora_config.vm.customize ["modifyvm", :id, "--memory", 1024]

  end
end
