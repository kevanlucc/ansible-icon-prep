# ansible-icon-prep-ha

Ansible playbooks and roles for the ICON Blockchain 

This role will configure nodes to be Highly available. manual testing can be done after deployment by stopping a node:
``` pcs cluster stop node1```
check the status with
``` pcs status```
and you will see the primary node is down, and the cluster IP has been switched over to the second node.


> To work with this repo, you need to install `meta` to pull in sub-repos 

### Prerequisites 

```bash
sudo apt install nodejs 
npm i -g meta 
meta git clone . # at the base of this repo 
pip install --user ansible 
```

### To run a playbook 

```bash
ansible-playbook  <ansible playbook yml>\
--inventory='X.X.X.X,' \
--user=ubuntu \
--become-method=sudo \
--become \
--forks=5 \
--private-key='~/.ssh/XXX'
```

### To run a role 

```bash
cd <role> 
ansible all \
-m include_role \
-a name=`pwd` \
--inventory='3.95.115.166,' \
--user=ubuntu \
--become-method=sudo \
--become \
--forks=5 \
--extra-vars='{"network_name":"testnet","keystore_path":"keystore","keystore_password":"testing1."}' \
--private-key='/home/rob/.ssh/testing'
```


## Current Status 

Right now we are deciding whether to switch to an ansible galaxy based approach to replace `meta`, keep it the way it is, or use a combination of all approaches.
