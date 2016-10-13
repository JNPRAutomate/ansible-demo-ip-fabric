
# Demo Ansible project to build an IP fabric using EBGP.  

This project is leveraging **roles** to build the configuration.
Each role will generate a part of the configuration.  
At the end all parts will be merged into a single file and eventually push to the device.

# How to start

1. Customize the inventory file [device.ini](device.ini)
2. Customize variables files in **host_vars** and **group_vars**
3. Run playbooks to generate and eventually deploy configuration

# Roles available

Roles can be found [here](roles)

### junos-system - configuration template

Junos-system will generate the main part of the configuration it will include all information needed to access the device (mgmt interface, password, account etc ...)

>Most variables are coming from the inventory or the file group_vars/all/common.yaml

### junos-ebgp - configuration template

junos-ebgp will generate all configuration to enable EBGP inside an IP Fabric.

> Most variables are specific to each device and need to be provided per device,
> You can find an example inside the role

# Playbooks available

To generate configuration for all leaf or spine (configuration are not push to device)
```
ansible-playbook -i devices.ini pb.config.all.yaml
```
All configurations will be available under the directory **config** at the root of the project.

To generate configuration for all devices and push them on devices
```
ansible-playbook -i devices.ini pb.config.all.commit.yaml
```
