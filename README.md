# Setting Up Local Dev Environment for PHP 7, MySQL 5 & Mongo 3
*  Toggle nginx configuration for Symfony 2 or Laravel 5 project (see below).

## General
* Provisioning has been tested on OS-X v10.11 with Ansible v1.9.6 and v2.0.2.0 

## Ansible
* Recommended installation is via Homebrew - http://brew.sh/ 
* http://effectif.com/mac-os-x/installing-specific-version-of-homebrew-formula
* `brew search ansible`
* `brew install homebrew/versions/ansible19` or `brew install homebrew/versions/ansible20`

## Edit the Vagrantfile
* Edit `config.vm.network "private_network", ip: "192.168.33.33"` if you want to change the IP of the Vagrant box.
* Edit `web_application_root_directory` to reflect the directory on the guest that will be used for this purpose (e.g., /var/www/your_app).
* Edit `config.vm.synced_folder "../{your_app}/"` and update the first argument to reflect the location of `{your_app}` on your host machine relative to `this` repo
    * you can just use the absolute path (e.g., `/Users/you/code/your_app`)
    
## Configure available parameters
* Edit `group_vars/all` if you want to configure:
    * an additional database user and database for mysql (defaults to false)
    * nginx configuration for Symfony 2 or Laravel 5 project (defaults to Symfony 2)
    * composer (defaults to true with dev settings)
    * xdebug (defaults to true but enabled only for fpm i.e., not cli)
     
## Run Vagrant up
* cd into the directory containing the `Vagrantfile`
    * e.g., `cd /Users/you/code/vagrantbox`
* Run `vagrant up`
     * This should completely provision the vagrant box and make your_app available at the IP address set in the Vagrantfile. 
* Add an entry to your `/etc/hosts` file if you want to use a domain name.
    * e.g., `192.168.33.33  your_app.local`
