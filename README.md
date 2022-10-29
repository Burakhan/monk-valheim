# Valheim Server & Monk
This repository contains Monk.io template to deploy Valheim & Monk either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/Burakhan/monk-valheim
```

## Load Template
```bash
cd monk-valheim
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-valheim
✔ Got the list
Type      Template                      Repository  Version  Tags
group     monk-vaultwarden/stack        local       -        -
runnable  monk-vaultwarden/vaultwarden  local       -        -
```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-vaultwarden/stack
? Select tag to run [local/monk-valheim/stack] on: mnk
✔ Starting the job: local/monk-valheim/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% ghcr.io/lloesche/valheim-server:latest mnk
✔ Checking/pulling images DONE
✔ Started local/monk-valheim/stack

🔩 templates/local/monk-valheim/stack
 └─🧊 Peer mnk
    └─🔩 templates/local/monk-valheim/valheim
       └─📦 63dd50a53af56ce150f28f7d22dd1daf-k-valheim-valheim-monk-valheim
          ├─🧩 ghcr.io/lloesche/valheim-server:latest
          ├─💾 /var/lib/monkd/volumes/growthbook -> /usr/local/src/app/packages/back-end/uploads
          ├─🔌 open udp 13.51.200.163:2456-2457 (0.0.0.0:2456-2457) -> 2456-2457
          └─🔌 open 13.51.200.163:9001 (0.0.0.0:9001) -> 9001

💡 You can inspect and manage your above stack with these commands:
	monk logs (-f) local/monk-valheim/stack - Inspect logs
	monk shell     local/monk-valheim/stack - Connect to the container's shell
	monk do        local/monk-valheim/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```
## Check admin gui

`http://13.49.137.107:8084/`



## Variables
The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| vault_port                    | Vault Warden port, Default: 8084 	               |
| vaultwarden_signup_enabled                    | Signup enable, Default: true 	               |
| vaultwarden_admin_token                    | admin password, Default: monk 	               |




## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```

```

    cap_add:
      - sys_nice
      
```