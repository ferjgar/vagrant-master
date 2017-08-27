GUEST_SYNC_FOLDER_PATH = "/var/www"

Vagrant.require_version ">= 1.9.8"

Vagrant.configure("2") do |config|

  # https://app.vagrantup.com/centos/boxes/7
  config.vm.box = "centos/7"

  config.vm.post_up_message = "WELCOME TO THE FERJGAR JUNGLE!!!"

  # at this moment, the default /vagrant shared folder will not sync by default (just an initial rsync)
  # between hosts on windows and virtualbox, so we need to setup a new one that magically should work
  # as expected and for all providers
  # IMPORTANT: note that we're supposing a folder structure here, so all the ferjgar repos should live
  # on the parent directory, something like:
  # /path/to/repos/repo1
  # /path/to/repos/repo2
  # /path/to/repos/vagrant-master
  # so in the guest, you'll be able to access local /path/to/repos in /var/www
  config.vm.synced_folder "./..", GUEST_SYNC_FOLDER_PATH
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # using local we don't need to install it on the host, vagrant should do it on the guest
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    # this a cool and clean way of installing required external ansible roles, thank you vagrant!
    ansible.galaxy_role_file = "requirements.yml"
    ansible.provisioning_path =  "#{GUEST_SYNC_FOLDER_PATH}/vagrant-master"
    ansible.extra_vars = { vagrant_synced_folder: GUEST_SYNC_FOLDER_PATH }
  end

  # so you can see ferjgar.github.io on http://localhost:6969
  config.vm.network :forwarded_port, guest: 4000, host: 6969

end
