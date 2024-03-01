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

## Hot to use
Ansible install SteamCMD, game server and start it in three tmux-sessions.
Use `tmux ls` for list running sessions.
* `DST-srv_dummy-session` — dummy session. It is used to correctly launch 
other two sessions.
* `DST-srv_Master` — Master session of server.
* `DST-srv_Caves` - Caves session of server.

For connect to specific tmux session use command
```console
dst_srv_user@server:~$ tmux a -t DST-srv_Master
```
For disconnect from tmux and leave DST server is running press `Ctrl+b`, `d`
This hotkeys is actual for default tmux configs.

## Known Issues

### After update DST client server is not visible
Update DST server (just play playbook again). SteamCMD update game server.

### tmux inside
Dont Starve Together server does not support management with remote console, 
when server work in the background. 
Therefore, I had to use tmux to preservation the ability use console.
If you know an analogue of `mcrcon` for DST, please let me know about it.
