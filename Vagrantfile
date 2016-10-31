# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  is_windows_host = (RUBY_PLATFORM =~ /mingw/) ? true : false

  config.vm.box = 'ubuntu/trusty64'
  config.vm.hostname = 'hitttenDevServer'

  config.vm.network 'private_network', ip: '192.168.2.100'

  config.ssh.forward_agent = true

  if is_windows_host #verify is if a windows host
    config.vm.synced_folder '.', '/vagrant', type: 'smb' #, :mount_options => ['dmode=775', 'fmode=664'] #TODO: vagrant ask password for admin user, this return "Error! Your console doesn't support hiding input. We'll ask for input again below, but we WILL NOT be able to hide input. If this is a problem for you, ctrl-C to exit and fix your stdin."
    config.vm.synced_folder '../..', '/home/vagrant/Workspace', type: 'smb' #, :mount_options => ['dmode=775', 'fmode=664']
  else
    config.vm.synced_folder '../..', '/home/vagrant/Workspace', type: 'nfs', :mount_options => ['actimeo=2', 'rw', 'vers=3', 'tcp', 'fsc']
  end

  config.vm.provider 'virtualbox' do |vb|
    vb.customize ['setextradata', :id, 'VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root', '1']
    vb.customize ['modifyvm', :id, '--memory', '2048']
    vb.name = 'hittten_dev_server'
  end

  # config.vm.provision 'file', source: '~/.gitconfig', destination: '.gitconfig'
  # config.vm.provision 'file', source: '~/.gitignore', destination: '.gitignore'
  # config.vm.provision 'file', source: '~/.ssh/id_rsa', destination: '.ssh/id_rsa'
  # config.vm.provision 'file', source: '~/.ssh/id_rsa.pub', destination: '.ssh/id_rsa.pub'
  # config.vm.provision 'file', source: '~/.ssh/known_hosts', destination: '.ssh/known_hosts'
  #
  # config.vm.provision 'shell', inline: 'chmod 400 .ssh/id_rsa'
  # config.vm.provision 'shell', inline: 'chmod 644 .ssh/id_rsa.pub'
  # config.vm.provision 'shell', inline: 'chmod 644 .ssh/known_hosts'

  if is_windows_host #verify is if a windows host
    config.vm.provision 'ansible_local' do |ansible|
      ansible.playbook = 'provision/vagrant.yml'
      ansible.install = true
    end
  else
    config.vm.provision :ansible do |ansible|
      ansible.playbook = 'provision/vagrant.yml'
    end
  end
end
