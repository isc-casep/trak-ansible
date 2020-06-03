# trak-ansible
TrakCare deployment with Ansible.
*Tested for TrakCare SYS 2020.*
Deployment for 1 DB server with exported NFS share and 2 web servers using those resources.

# Usage

## Clone the repo

 ```
git clone git@github.com:isc-casep/trak-ansible.git
```

## enter the repo
```
 cd trak-ansible
```

## edit the main variables
```
 vi hosts
 vi group_vars/all/vars-db_server.yml
 vi group_vars/all/vars-standard-defaults.yml
 vi group_vars/all/vars-start-here.yml
```
## fire!
```
 ansible-playbook site.yml
```
*remember to have ssh key based authentication enabled beforehand*

# Preparation for nodes

## create user
```
 useradd deployment -c "Ansible Deployment" -G wheel
```
## change to the user
```
 su - deployment
```
## enable key-base authentication (replace contents of your own .pub here)
```
 mkdir .ssh ; chmod 700 .ssh ; echo "{{contents of your own .pub key}}" > .ssh/authorized_keys ; chmod 600 .ssh/authorized_keys
```
See [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) for further reference.

# Considerations
The path for the local installers (on the ansible machine) is defined on *local_installers_path* (vars-start-here.yml)

Most relevant files:

Web Gateway: *webgateway_installer*, tested with: WebGateway-2020.1.0.215.0-lnxrhx64.tar.gz

IRIS: *iris_version*, tested with: IRISHealth-2020.1.0.215.0-lnxrhx64.tar.gz

TrakCare: *trak_installer_filename*, tested with: T2020_20200401_0909_R0_SYS_FULL_B14.zip
