# eLANman on localhost


### What is this
This project aim is to help admins configure WHM/cPanel servers using Ansible.

#### What does it do
Currently you can do the following tasks with this project:  
Configure WHM tweaks for the following:  
 Authentication Providers  
 Market Provider  
Install and configure ConfigServer firewall, csf  
Install ConfigServer Mail Queue Manage plugin  
Install ConfigServer Mail Manage plugin  
Install ConfigServer ModSecurity Manage plugin  
Configure CloudLinux CageFS,Alt-php,LSAPI  

#### Based on
The directory structure is based on [Playboooks Best Practices](http://docs.ansible.com/ansible/playbooks_best_practices.html) and defines 6 roles, 3 inventory files and 5 regions.


### Why
The main reason for this project was to enable me to create a baseline for new servers and slowly reconfigure old servers according to baseline.

### How
The structure takes into account 6 roles:  
  common - common role, included in all roles first (This role is an addon to all roles)  
  sharedhosting - Shared hosting servers   
  dnsonly - whm dnsonly install for dns clustering   
  mailonly - Mail only whm servers   
  ftponly - FTP only whm servers   
  postrun - postrun role, included in all roles last (This role is an addon to all roles)  

#### Files layout
.   
* files
* group_vars
* host_vars
* roles
    * common
        * defaults
        * files
        * handlers
        * meta
        * tasks
        * templates
        * vars
    * dnsonly
        * defaults
        * files
        * handlers
        * meta
        * tasks
        * templates
        * vars
    * mailonly
        * defaults
        * files
        * handlers
        * meta
        * tasks
        * templates
        * vars
    * sharedhosting
        * defaults
        * files
        * handlers
        * meta
        * tasks
        * templates
        * vars


## Install

### Ansible
How ansible works:  
You write your stuff in almost plain language compatible with ansible (yml) and ansible fire commands using ssh, no agent is required.  
It might be slow for large quantities and for the purpose of this project it's not a problem.  

#### Manage machine
You can use a virtual machine with very low resources as your work tool, keep your custom changes in a private git and shut it down when finished.  
Install ansible machine  
yum-ish way:  
`sudo yum install epel-release`  
`sudo yum install ansible`  
apt-ish way:  
`sudo apt-get install software-properties-common`  
`sudo apt-add-repository ppa:ansible/ansible`  
`sudo apt-get update`  
`sudo apt-get install ansible`  
More info at:  
http://docs.ansible.com/ansible/latest/intro_installation.html  

### ssh Infrastructure
#### generate keys
how to generate keys  
ssh-keygen -t rsa  
#### copy public keys
how to copy keys to hosts  
ssh-copy-id ip/hostname 

