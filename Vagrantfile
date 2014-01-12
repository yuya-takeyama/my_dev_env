Vagrant.configure('2') do |config|
  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      oh_my_zsh: {
        users: [{
          login: 'vagrant',
          theme: 'daveverwer',
          plugins: %w|git git-flow bundler tmux screen gem pip npm tmuxinator vagrant|,
        }],
      },
      rbenv: {
        user_installs: [
          {
            user: 'vagrant',
            rubies: ['2.0.0-p353'],
            global: '2.0.0-p353',
            gems: {
              '2.0.0-p353' => [
                {name: 'bundler'},
                {name: 'rails'},
              ],
            },
          },
        ]
      },
    }

    chef.run_list = [
      'recipe[apt]',
      'recipe[base_packages]',
      'recipe[dotfiles]',
      'recipe[oh_my_zsh]',
      'recipe[ruby_build]',
      'recipe[rbenv::user]',
      'recipe[phpdev]',
      'recipe[composer]',
    ]
  end
end
