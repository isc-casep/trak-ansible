# trak-ansible
TrakCare deployment with Ansible


# Usage

## Clone the repo

 git clone git@github.com:isc-casep/trak-ansible.git

## enter the repo

 cd trak-ansible

## edit the main variables 

 vi hosts
 vi group_vars/all/vars-db_server.yml
 vi group_vars/all/vars-standard-defaults.yml
 vi group_vars/all/vars-start-here.yml

## fire!

 ansible-playbook site.yml

*remember to have ssh key base authentication beforehand*

# Preparation for nodes

## create user

 useradd deployment -c "Ansible Deployment" -G wheel

## change to the user

 su - deployment 

## enable key-base authentication (replace contents of your own .pub here)

 mkdir .ssh ; chmod 700 .ssh ; echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDMLIqzUJ2x56BE4TzZZAjemc3V9stwB+TMGqBZsTTZVBSOWRzesaNOPnFmXZ4adJjRJoHV+OZm5vbkVb05Tq2XyDZIp7mXFfpMGo0Ucq+eQL7qo7O15jjwQxnWbeY4qUk5RuFEObiykxggFelGtz8mSnxMATyWSgO8BPmlGih+ZEIshLBF7z5CYHRU45ZbaTcVpoAJx+FR+U/qj6Qk8EnMm2WHgZ2Od9gVd0d/qAstlAsrcSWuqI5FDLUl2VvPkuBmeMrL0JCWVa8T6Mfa83j15X7PMtWEqrnNcELdwQS3wUrVTcNJvCn+8hQ3YXsN1nfbToAtfx6WRBxCsbWGOfvh casep@ansible" > .ssh/authorized_keys ; chmod 600 .ssh/authorized_keys

