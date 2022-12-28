# toni.inventorie
This inventorie is used to setup dedicated server as 1-node docker swarm
For simplicity i always use docker in swarm mode. In serious setups use kubernetes.

### Usage
This repository can be used to install most of the toni.* 
The purpose is to get easily started. Its primary purpose is to help with installation of toni.corteza

Before doin so, change to root on your installer machine. (WSL2 or any Linux machine)

```bash
sudo su -
```

After cloneing the repositorie you only have to adjust the targets.yml. Your are good to go if you change the domain to whatever domain you are using on your server and letsencrypt mail, but i would expect you change the openresty and keycloak values as well, cause i use both a lot.

```bash
nano <inventorie role dir>/server/group_vars/targets.yml
```

These repo cannot be used on its own, so head over to cloning [Corteza role](https://github.com/tnissen375/toni.corteza)

### Example useage in conjunction with toni.corteza role
```bash
ansible-playbook install.yml -i ../toni.inventorie/server --vault-id corteza@vault --tags "keycloak, kc_realm" --skip-tags "kc_role" --extra-vars "ansible_ssh_host=<YOUR SERVER IP>"
```