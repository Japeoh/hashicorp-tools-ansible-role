# Hashicorp Tools Ansible Role

Installs Hashicorp's tools

*   [Consul](https://www.hashicorp.com/products/consul/)
*   [Nomad](https://www.hashicorp.com/products/nomad/)
*   [Packer](https://www.packer.io/)
*   [Terraform](https://www.hashicorp.com/products/terraform/)
*   [Vagrant](https://www.vagrantup.com/)
*   [Vault](https://www.hashicorp.com/products/vault/)

Installation of each tool is disabled by default allowing the selection of only the desired tool(s).

The tool(s) will be downloaded into folders created in the base directory and named _toolname-version_ e.g. _consul-1.7.1_

## Variables

| Variable                    | Description                                        | Default Value
|-----------------------------|----------------------------------------------------|---|
| hashicorp_tools_base_dir    | The tool specific directories will be created here | ~/tools
| hashicorp_tools_install_dir | The directory where the binaries will be installed | ~/bin

Installation of the various tools can be enabled by switching the following variables to `yes`

| Variable                  | Description       | Default Value
|---------------------------|-------------------|---|
| hashicorp_tools_consul    | Install Consul    | no
| hashicorp_tools_nomad     | Install Nomad     | no
| hashicorp_tools_packer    | Install Packer    | no
| hashicorp_tools_terraform | Install Terraform | no
| hashicorp_tools_vagrant   | Install Vagrant   | no
| hashicorp_tools_vault     | Install Vault     | no

The specific version to be installed can be controlled by providing the version number and checksum.

| Variable                           | Default Value |
|------------------------------------|---|
| hashicorp_tools_consul_version     | 1.7.1
| hashicorp_tools_consul_checksum    | sha256:09f3583c6cd7b1f748c0c012ce9b3d96de95a6c0d2334327b74f7d72b1fa5054
| hashicorp_tools_nomad_version      | 0.10.4
| hashicorp_tools_nomad_checksum     | sha256:7b12ff24c9ff592978d4c5b5ea06f60bb0aa679055a356b7898e480f0ba63d63
| hashicorp_tools_packer_version     | 1.5.4
| hashicorp_tools_packer_checksum    | sha256:c7277f64d217c7d9ccfd936373fe352ea935454837363293f8668f9e42d8d99d
| hashicorp_tools_terraform_version  | 0.12.23
| hashicorp_tools_terraform_checksum | sha256:78fd53c0fffd657ee0ab5decac604b0dea2e6c0d4199a9f27db53f081d831a45
| hashicorp_tools_vagrant_version    | 2.2.7
| hashicorp_tools_vagrant_checksum   | sha256:55435d8b146e6df5dcda71c0df50ddd7530aeb34b26b016fb433b8332e4a69c5
| hashicorp_tools_vault_version      | 1.3.2
| hashicorp_tools_vault_checksum     | sha256:6e72132de0421b74d909f50be1823fe57182694c4268ba9a38c31213d9497ec9

## Example Playbook

```yaml
- hosts: localhost
  become: yes
  roles:
    - japeoh.hashicorp_tools
      vars:
        hashicorp_tools_install_dir: /usr/local/bin
        hashicorp_tools_consul: yes
        hashicorp_tools_vauly: yes
```
    
## License

GPLv3

##  Development

See [here](https://github.com/japeoh/ansible-role-development) for setup.

Because of the FUSE requirements for Vagrant, a more privileged container is required. To keep this isolated a seperate
Molecule scenario has been created for Vagrant.

To run all scenarios execute

```bash
molecule test --all
```

To just run Vagrant execute

```bash
molecule test -s vagrant
```