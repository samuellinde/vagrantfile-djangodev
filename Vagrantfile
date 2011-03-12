Vagrant::Config.run do |config|
  config.vm.box = "lucid32"
  config.vm.box_url = "http://files.vagrantup.com/lucid32.box"

  config.vm.network "33.33.33.10"
  config.vm.forward_port "http", 8000, 8000

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "~/Dropbox/Developer/cookbooks"
    chef.add_recipe "git"
    chef.add_recipe "python"
    chef.add_recipe "sqlite"
    chef.add_recipe "subversion"
    chef.add_recipe "django_dev"
  
    # You may also specify custom JSON attributes:
    # chef.json = { :mysql_password => "foo" }
    chef.json.merge!({
        :python_global_packages => ["yolk", "PIL", "Markdown", "sorl-thumbnail", "-e svn+http://code.djangoproject.com/svn/django/trunk#egg=Django"],
        # :python_packages => ["MySQL-python"],
        :python_packages => [],
        
    })
  end
end
