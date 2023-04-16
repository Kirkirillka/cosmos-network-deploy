# Ansible for Cosmos Node

Cosmos Node `gaia` installed via Ansible.

Here is a list of defined playbooks:

- `cosmos-node-hardening.yml` - harden the target Node OS to improve security. Applies best practises for running Cosmos Network Node.
- `cosmos-node-install.yml` - build, install and configure `gaiad`. You can connect to testnet or mainnet by changing role's values in `inventory`.
- `cosmos-node-tendermint-exporter.yml` - install a custom Tendermint Exporter.
- `cosmos-node-nginx.yml` - install and configure Nginx on a Cosmos Node.
- `cosmos-node.yml` - applies all the playbooks above to completely prepare a working Cosmos Node.


## Quickstart

1. Install Ansible dependencies

```
ansible-galaxy install -r requirements.yml
```

2. Configure `inventory`. You may change the values according to the roles defaults. Please, check out Ansible roles in custom `roles` or defined in `requirements.yml`

3. Run the full Cosmos Node installation playbook:

```
ansible-playbook -i inventory/cosmos-net/hosts.ini cosmos-node.yml
```