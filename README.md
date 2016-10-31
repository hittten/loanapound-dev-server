# Ansible provisioning

Ubuntu 15.10 LTS virtual environment for web apps via Vagrant and Ansible.

## Installed tools

+ [Git](http://git-scm.com)
+ [Vim](http://www.vim.org)
+ [Apache2](http://www.apache.org/)
+ [PHP5](http://php.net/)
+ [PHP-FPM](http://php-fpm.org/)
+ [nodeJS](https://nodejs.org/)
+ [mongoDB](https://www.mongodb.com/)
+ [MySQL](http://www.mysql.com/)
+ [Elastic Search](https://www.elastic.co/)

Linux packages:

 + curl
 + wget
 + ntp
 + htop

## Requirements

You must have installed the following tools in order to work:

+ [VirtualBox](https://www.virtualbox.org/)
+ [Vagrant](https://www.vagrantup.com/)
+ [Ansible](http://www.ansible.com/home)

## How to install Vagrant and Ansible?

### Ubuntu/Debian Linux
#### With Vagrant and VirtualBox (all stuff in a new virtual machine, nothing is in your local machine):
```bash
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install git vagrant ansible virtualbox virtualbox-guest-additions-iso
```
Go to your workspace directory
```bash
git clone git@github.com:hittten/loanapound-dev-server.git
cd dev-server
vagrant up
```

### OSX
````bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install caskroom/cask/brew-cask
brew cask install vagrant
brew cask install virtualbox
brew install ansible
````
Go to your workspace directory
```bash
git clone git@github.com:hittten/loanapound-dev-server.git
cd loanapound-dev-server
vagrant up
```

### Windows
Download and install both programs:
+ [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
+ [Vagrant](https://www.vagrantup.com/downloads.html)
+ [Git](https://git-scm.com/download/win)

Ansible is not compatible with Windows, so do not install it.
Open git bash as an administrator, go to workspace directory:
```bash
git clone git@github.com:hittten/loanapound-dev-server.git
cd loanapound-dev-server
vagrant up
```

## Notes
This server install two projects, please see the README:
+ [Loan API](https://github.com/hittten/loanapound-api)
+ [Loan Board](https://github.com/hittten/loanapound-board)
