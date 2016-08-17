$script = <<SCRIPT
sudo apt-get remove unattended-upgrades -y
sudo add-apt-repository ppa:ansible/ansible
sudo apt-get update -y
sudo apt-get install git vim ansible -y
ansible-playbook /vagrant/setup.yml
SCRIPT

Vagrant.configure("2") do |config|
  # https://atlas.hashicorp.com/boxcutter/boxes/ubuntu1604-desktop
  config.vm.box = "boxcutter/ubuntu1604-desktop"

  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "setup.yml"
  # end
  #

  config.vm.provision "shell", inline: $script

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "2048"
  end

end

