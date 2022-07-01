## DevOps Demo

This repo demonstrated Infrastructure as Code using Vagrant and Ansible.

### Install VirtualBox

Get it from [here](https://www.virtualbox.org/wiki/Downloads)

### Install Vagrant

Get it from [here](https://www.vagrantup.com/downloads)

### Install Ansible

Get it from [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

### Get this repo

Clone this repo onto your laptop. `cd` into the repo's top level directory.

Open the VirtualBox UI so you can see the machines being created.

` $ vagrant up --provision`

When the three machines are running, log in to each of them in a separate terminal window and tail the logs

```
$ vagrant ssh balancer
% sudo tail -f /var/log/haproxy.log
:
$ vagrant ssh backend1
% sudo tail -f sudo tail -f /var/log/apache2/access.log
:
$ vagrant ssh backend2
% sudo tail -f sudo tail -f /var/log/apache2/access.log
:
```
Hit the load balancer in a browser http://192.168.56.17 and see the entry in the LB log and one of the backend logs. Hit Refresh the page and see the LB entry and an entry in the other backend log.

