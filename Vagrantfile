Vagrant.configure('2') do |config|
  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'

  config.vm.provision :chef_solo do |chef|
    chef.run_list = [
      'recipe[apt]',
      'recipe[base_packages]',
      'recipe[dotfiles]',
    ]
  end
end
