VAGRANTFILE_API_VERSION = "2"

def define_standard_vm(config, host_name, ip)
  config.vm.define host_name do |config|
    config.vm.box = 'precise64'
    config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
    config.vm.host_name = "#{host_name}.adblockplus.org"
    config.vm.network :private_network, ip: ip
    config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--cpus", 1]

      # Work around https://www.virtualbox.org/ticket/11649
      vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    end

    config.vm.provision :shell, :inline => '
if ! test -f /usr/bin/puppet; then
  sudo apt-get update && sudo apt-get install -y puppet
fi'

    manifest_files = ['vagrant.pp', 'nodes.pp']
    manifest_files.each do |manifest_file|
      config.vm.provision :puppet do |puppet|
        puppet.options = ['--environment=development']
        puppet.manifests_path = 'manifests'
        puppet.manifest_file = manifest_file
        puppet.module_path = 'modules'
      end
    end

    yield(config) if block_given?
  end
end

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  define_standard_vm config, 'server4', '10.8.0.99'
  define_standard_vm config, 'server5', '10.8.0.100'
  define_standard_vm config, 'server6', '10.8.0.101'
  define_standard_vm config, 'server7', '10.8.0.102'
  define_standard_vm config, 'server10', '10.8.0.105' do |config|
    config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 1024]
    end
  end
  define_standard_vm config, 'server11', '10.8.0.106'
  define_standard_vm config, 'server12', '10.8.0.107'
  define_standard_vm config, 'server15', '10.8.0.110'
  define_standard_vm config, 'server19', '10.8.0.114'
  define_standard_vm config, 'notification1', '10.8.0.118'
  define_standard_vm config, 'notification2', '10.8.0.119'
  define_standard_vm config, 'filter1', '10.8.0.120'
  define_standard_vm config, 'filter2', '10.8.0.121'
  define_standard_vm config, 'filter3', '10.8.0.122'
  define_standard_vm config, 'filter4', '10.8.0.123'
  define_standard_vm config, 'filter5', '10.8.0.124'
  define_standard_vm config, 'filter6', '10.8.0.125'
  define_standard_vm config, 'download1', '10.8.0.126'
  define_standard_vm config, 'filtermaster1', '10.8.0.127'
  define_standard_vm config, 'update1', '10.8.0.128'
  define_standard_vm config, 'web1', '10.8.0.129'
  define_standard_vm config, 'stats1', '10.8.0.130'
  define_standard_vm config, 'issues1', '10.8.0.131'
  define_standard_vm config, 'codereview1', '10.8.0.132'
  define_standard_vm config, 'filter7', '10.8.0.133'
  define_standard_vm config, 'filter8', '10.8.0.134'
  define_standard_vm config, 'filter9', '10.8.0.135'
  define_standard_vm config, 'filter10', '10.8.0.136'
  define_standard_vm config, 'filter11', '10.8.0.137'
  define_standard_vm config, 'filter12', '10.8.0.138'
  define_standard_vm config, 'filter13', '10.8.0.139'
  define_standard_vm config, 'filter14', '10.8.0.140'
  define_standard_vm config, 'filter15', '10.8.0.141'
  define_standard_vm config, 'filter16', '10.8.0.142'
  define_standard_vm config, 'filter17', '10.8.0.143'
  define_standard_vm config, 'filter18', '10.8.0.144'
end
