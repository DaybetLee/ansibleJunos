# ansibleJunos
This project serve to show the examples of Ansible Junos modules.
Following are the steps require to make Ansible work in Ubuntu 20.04.

1. Install pip for Python 3 on Ubuntu 20.04
  ```sh
  sudo apt update
  sudo apt install python3-pip
  ```
Verify the pip version
```sh
pip3 --version
```
2. Install Ansible
```sh
python -m pip install --user ansible
```
Verify ansible is working
```sh
ansible localhost -m ping
```
3. Add device to service host file (DNS) [Optional]

Navigate to `sudo nano /etc/hosts` to add the device

Sample:

`172.16.104.117/20 ex4300`

Verify by doing `ping ex4300`

4. Create SSH key in ubuntu.
```sh
ssh-keygen
```

Verify the keys by doing `ls .ssh`

5. In the same ubuntu directory, access and copy the public key file `.ssh/id_rsa.pub` in detail. Access the juniper device and add the ubuntu public key using the following sample command.

`set system login user ansible authentication ssh-rsa "ssh-rsa AAAAB3NzaC1yc2.....ZR6q92bI6yYSc= ansible@ansible-virtual-machine"`

6. Add device to ansible inventory by navigating to `sudo nano /etc/ansible/hosts`

Sample:

[junos-switches]

ex4300

or 

[junos-switches]

172.16.104.117/20

7. Download ncclient module

```sh
pip install ncclient
```

8. Enable netconf in the juniper device. 

```sh
set system services netconf ssh
```

Update 2 Feb 2021:: Finding time to go through each and every junos module and adding the sample here.
