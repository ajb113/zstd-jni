$script = <<-SCRIPT
dpkg --add-architecture armhf
sed -i 's/deb/deb [arch=amd64]/' /etc/apt/sources.list
echo "deb [arch=armhf] http://ports.ubuntu.com/ bionic main universe" | tee -a /etc/apt/sources.list
apt update
apt install -y crossbuild-essential-armhf cmake gcc-arm-linux-gnueabihf
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provision "shell", inline: $script
end
