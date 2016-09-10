About
=====

fuel.yaml
---------

Install Fuel via RPM packages:

* take node with CentOS 7 minimal install;

* specify its IP in `./hosts` file:

        fuel-node ansible_ssh_host=IP ansible_ssh_user=root

* run playbook:

        $ ansible-playbook fuel.yaml

Parameters are hardcoded in `roles/fuel/vars/main.yaml` and
`roles/fuel/defaults/main.yaml`.

os.yaml
-------

os_client role can be used to create the following network setup in
Openstack tenant:

![Network scheme](/os-networks.png?raw=true "Network scheme")

To run the playbook you need os-manager node: simply any instance with
python-openstackclient installed. No root access required.

* set ip address and user for os-manager node in `./hosts` file:

        os-manager ansible_ssh_host=IP ansible_ssh_user=USER

* source the openrc.sh file with credentials for empty openstack
  tenant:

        $ source ./openrc.sh

* update tenant-specific parameters in `roles/os_client/vars/main.yaml`;

* run playbook:

        $ ansible-playbook os.yaml
