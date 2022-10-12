Vagrant.configure("2") do |config|
  config.vm.define "jammy" do |c|
    c.vm.box = "ubuntu/jammy64"
    c.vm.network "forwarded_port", guest: 3000, host: 3000
    c.vm.provision "shell", inline: <<-SCRIPT
wget -qO- https://dl.packager.io/srv/pghero/pghero/key | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/pghero.list \
  https://dl.packager.io/srv/pghero/pghero/master/installer/ubuntu/22.04.repo
sudo apt-get update
sudo apt-get -y install pghero
sudo pghero config:set PORT=3000
sudo pghero config:set DATABASE_URL=postgres://10.0.2.2/pghero_test
sudo pghero scale web=1
sudo service pghero restart
    SCRIPT
  end

  config.vm.define "focal" do |c|
    c.vm.box = "ubuntu/focal64"
    c.vm.network "forwarded_port", guest: 3001, host: 3001
    c.vm.provision "shell", inline: <<-SCRIPT
wget -qO- https://dl.packager.io/srv/pghero/pghero/key | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/pghero.list \
  https://dl.packager.io/srv/pghero/pghero/master/installer/ubuntu/20.04.repo
sudo apt-get update
sudo apt-get -y install pghero
sudo pghero config:set PORT=3001
sudo pghero config:set DATABASE_URL=postgres://10.0.2.2/pghero_test
sudo pghero scale web=1
sudo service pghero restart
    SCRIPT
  end

  config.vm.define "bionic" do |c|
    c.vm.box = "ubuntu/bionic64"
    c.vm.network "forwarded_port", guest: 3002, host: 3002
    c.vm.provision "shell", inline: <<-SCRIPT
wget -qO- https://dl.packager.io/srv/pghero/pghero/key | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/pghero.list \
  https://dl.packager.io/srv/pghero/pghero/master/installer/ubuntu/18.04.repo
sudo apt-get update
sudo apt-get -y install pghero
sudo pghero config:set PORT=3002
sudo pghero config:set DATABASE_URL=postgres://10.0.2.2/pghero_test
sudo pghero scale web=1
sudo service pghero restart
    SCRIPT
  end

  config.vm.define "bullseye" do |c|
    c.vm.box = "debian/bullseye64"
    c.vm.network "forwarded_port", guest: 3003, host: 3003
    c.vm.provision "shell", inline: <<-SCRIPT
sudo apt-get -y install apt-transport-https
wget -qO- https://dl.packager.io/srv/pghero/pghero/key | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/pghero.list \
  https://dl.packager.io/srv/pghero/pghero/master/installer/debian/8.repo
sudo apt-get update
sudo apt-get -y install pghero
sudo pghero config:set PORT=3003
sudo pghero config:set DATABASE_URL=postgres://10.0.2.2/pghero_test
sudo pghero scale web=1
sudo service pghero restart
    SCRIPT
  end

  config.vm.define "centos7" do |c|
    c.vm.box = "centos/7"
    c.vm.network "forwarded_port", guest: 3004, host: 3004
    c.vm.provision "shell", inline: <<-SCRIPT
sudo wget -O /etc/yum.repos.d/pghero.repo \
  https://dl.packager.io/srv/pghero/pghero/master/installer/el/7.repo
sudo yum -y install pghero
sudo pghero config:set PORT=3004
sudo pghero config:set DATABASE_URL=postgres://10.0.2.2/pghero_test
sudo pghero scale web=1
sudo service pghero restart
    SCRIPT
  end
end
