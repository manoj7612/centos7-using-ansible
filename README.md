# centos7-using-ansible

# Description
Install development environment in CentOS 7 machine using Ansible


# Installation:
Download Centos 7.8 images from the following url:

http://centos.mirror.snu.edu.in/centos/7.8.2003/isos/x86_64/CentOS-7-x86_64-DVD-2003.iso

Do a minimal install by following the on-screen instructions.  

Ansible must be installed in another machine from which you need to run the playbooks for installing the required packages.  

Adapt the hosts file of Ansible with the IP addresses or hostnames of destination servers.  In the following hosts configuration, considering that the hostname of the CentOS machine installed in above steps is 'test.example.com', write 'test.example.com' under [servers] as shown below:

```
vi /etc/ansible/hosts

[servers]
test.example.com

```
Create an SSH Key Pair for authentication.

```
ssh-keygen

```

Once an SSH key has been created, copy the key to the server: test.example.com
```
ssh-copy-id root@test.example.com

```

# Usage
 
```
ansible-playbook playbooks/main.yml -v

``` 

# Post Installation instructions

Once the run of the playbook main.yml is finished, the configuration towards the Database - 'MySQL', Web servers - 'Apache' and 'Nginx' need to be done.

These services must be enabled to restart at boot time.

```
systemctl enable httpd.service
systemctl enable nginx.service
systemctl enable mysqld.service
reboot
```

# Contributing

Contributions are welcome!

# License

GNU General Public License v3.0
