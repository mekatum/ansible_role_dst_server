# Ansible role for deploy self-hosted vanilla Dont Starve Together server

This Ansible role deploy self-hosted Dont Starve Together server.

## System requirements

So to run the playbook you will need:
* Ansible 2.12 or newer on management node
* Ubuntu 22.04 or newer with python3 installed on managed node


```yaml
- hosts: dst.your-domain.local
  roles:
    - dst
  become: True
```

And run this playbook with `ansible-playbook`
```console
user@host:~$ ansible-playbook dst.yaml
```

## Default vars
* `dst_srv_user` — user, who run server
* `dst_srv_comment` — user comment
* `dst_srv_steamcmd_url` — SteamCMD URL
* `dst_srv_game_dir` — dir for server's data
* `dst_srv_cluster_name` — cluster name
