# Kwuxlab-ansible-common-tailscale

This playbook installs and configures tailscale for the target node(s).

## Requirements

Configure your tailscale authorization key as shown in `vars/example_environment.yml`.

The playbook will look for a credential file in `vars/` that matches the ansible
environment, *e.g.*:

- `production_environment.yml`
- `test_environment.yml`
- etc.

One way to secure these files is to encrypt them files with `ansible-vault`:

```sh
KWUXLAB_ENV="production"; ansible-vault encrypt \
  --vault-id password_file."${KWUXLAB_ENV}".txt \
  playbooks/kwuxlab_ansible_common_tailscale/vars/"${KWUXLAB_ENV}"_environment.yml
```

Which requires that `password_file."${KWUXLAB_ENV}".txt` 
(read: `password_file.production.txt` in the above example) exists in your
current directory.