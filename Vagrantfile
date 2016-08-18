$script = <<SCRIPT
wait_for_apt_lock () {
  while [ ! -f /var/lib/dpkg/lock ]
  do
    sleep 2
  done
}
sudo apt-get remove unattended-upgrades -y
wait_for_apt_lock
sudo add-apt-repository ppa:ansible/ansible
wait_for_apt_lock
sudo apt-get update -y
wait_for_apt_lock
sudo apt-get install git vim ansible -y

cp /vagrant/setup.yml /vagrant/setup_vagrant.yml
cp /vagrant/vars.yml /vagrant/vars_vagrant.yml

sed -i "s/user:.*/user: vagrant/g" /vagrant/vars_vagrant.yml
sed -i "s/vars.yml*/vars_vagrant.yml/g" /vagrant/setup_vagrant.yml

ansible-playbook /vagrant/setup_vagrant.yml

rm /vagrant/vars_vagrant.yml
rm /vagrant/setup_vagrant.yml
SCRIPT

Vagrant.configure("2") do |config|
  # https://atlas.hashicorp.com/boxcutter/boxes/ubuntu1604-desktop
  config.vm.box = "boxcutter/ubuntu1604-desktop"
  # config.vm.box = "bento/ubuntu-16.04"

  # config.vm.provision "ansible" do |ansible|
  #   ansible.playbook = "setup.yml"
  # end
  #
  #config.vm.provision "ansible_local" do |ansible|
  #   ansible.playbook = "setup.yml"
  # end

  config.vm.provision "shell", inline: $script

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "2048"
  end
end

