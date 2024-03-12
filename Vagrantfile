Vagrant.configure("2") do |config|

  # name the VMs
  config.vm.define "rocky9" do |node|

    # which image to use
    node.vm.box = "rockylinux/9"

    # sizing of the VMs
    node.vm.provider "libvirt" do |lv|
      lv.memory = 4096
      lv.cpus = 2
    end

    # set the hostname
    node.vm.hostname = "rocky9"

    # disable the shared folder
    node.vm.synced_folder ".", "/vagrant", disabled: true

    node.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.groups = {
        "simple"  => [ "rocky9" ]
      }
      ansible.playbook = "ansible/playbook-vagrant.yml"
    end # node.vm.provision

  end # config.vm.define servers

end # Vagrant.configure
