# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
provision_script = <<SCRIPT
pushd /tmp &> /dev/null
wget http://s3.amazonaws.com/influxdb/influxdb-latest-1.x86_64.rpm
yum install -y ./influxdb-latest-1.x86_64.rpm
popd &> /dev/null
systemctl start influxdb
SCRIPT

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'chef/centos-7.0'

  config.vm.provision 'shell', inline: provision_script
  config.vm.network 'forwarded_port', guest: 8083, host: 8083
  config.vm.network 'forwarded_port', guest: 8086, host: 8086
end
