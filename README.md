# Airbyte & Monk
This repository contains Monk.io template to deploy Airbyte & Monk either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

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
git clone https://github.com/Burakhan/monk-airbyte
```

## Load Template
```bash
cd monk-airbyte
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-airbyte
✔ Got the list
Type      Template                         Repository  Version  Tags
runnable  monk-airbyte/airbyte-bootloader  local       -        -
runnable  monk-airbyte/airbyte-cron        local       -        -
runnable  monk-airbyte/airbyte-db          local       -        -
runnable  monk-airbyte/airbyte-init        local       -        -
runnable  monk-airbyte/airbyte-server      local       -        -
runnable  monk-airbyte/airbyte-temporal    local       -        -
runnable  monk-airbyte/airbyte-webapp      local       -        -
runnable  monk-airbyte/airbyte-worker      local       -        -
group     monk-airbyte/stack               local       -        -
```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-airbyte/stack
✔ Starting the job: templates/local/monk-airbyte/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% airbyte/init:0.40.18 monk
✔ [================================================] 100% airbyte/bootloader:0.40.18 monk
✔ [================================================] 100% airbyte/db:0.40.18 monk
✔ [================================================] 100% airbyte/worker:0.40.18 monk
✔ [================================================] 100% airbyte/cron:0.40.18 monk
✔ [================================================] 100% airbyte/webapp:0.40.18 monk
✔ [================================================] 100% airbyte/temporal:0.40.18 monk
✔ [================================================] 100% airbyte/server:0.40.18 monk
✔ Checking/pulling images DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ Updating containers DONE
✔ ✨ templates/local/monk-airbyte/stack updated successfully

🔩 templates/local/monk-airbyte/stack
 └─🧊 Peer monk
    ├─🔩 templates/local/monk-airbyte/airbyte-webapp
    │  └─📦 ea9a7a9f9ce23c4640a8d8858d4b80ed--airbyte-airbyte-webapp-webapp
    │     ├─🧩 airbyte/webapp:0.40.18
    │     └─🔌 open 16.16.26.126:80 (0.0.0.0:80) -> 80
    ├─🔩 templates/local/monk-airbyte/airbyte-cron
    │  └─📦 2fb451fdb57e4a509ca0f9d22755841a-monk-airbyte-airbyte-cron-cron
    │     ├─🧩 airbyte/cron:0.40.18
    │     └─💾 /var/lib/monkd/volumes/airbyte/tmp/workspace -> /tmp/workspace
    ├─🔩 templates/local/monk-airbyte/airbyte-temporal
    │  └─📦 e63afed309607b83495ac44721969158-byte-airbyte-temporal-temporal
    │     ├─🧩 airbyte/temporal:0.40.18
    │     └─🔌 open 16.16.26.126:7233 (0.0.0.0:7233) -> 7233
    ├─🔩 templates/local/monk-airbyte/airbyte-init
    │  └─📦 4d881eb584197b08166cb7ed0d7e75a0-monk-airbyte-airbyte-init-init
    │     ├─🧩 airbyte/init:0.40.18
    │     ├─💾 /var/lib/monkd/volumes/airbyte/tmp -> /local_parent
    │     └─🔌 open 16.16.26.126:8001 (0.0.0.0:8001) -> 7000
    ├─🔩 templates/local/monk-airbyte/airbyte-server
    │  └─📦 9a23972956087203d3d3d630f5e6be97--airbyte-airbyte-server-server
    │     ├─🧩 airbyte/server:0.40.18
    │     ├─💾 /var/lib/monkd/volumes/airbyte/tmp/airbyte_local -> /tmp/airbyte_local
    │     ├─💾 /var/lib/monkd/volumes/airbyte/tmp/workspace -> /tmp/workspace
    │     └─🔌 open 16.16.26.126:9001 (0.0.0.0:9001) -> 9000
    ├─🔩 templates/local/monk-airbyte/airbyte-worker
    │  └─📦 12c1928c06e7753274207c69c4202cb1--airbyte-airbyte-worker-worker
    │     ├─🧩 airbyte/worker:0.40.18
    │     ├─💾 /var/lib/monkd/volumes/airbyte/tmp/airbyte_local -> /tmp/airbyte_local
    │     ├─💾 /var/lib/monkd/volumes/airbyte/tmp/workspace -> /tmp/workspace
    │     └─🔌 open 16.16.26.126:9000 (0.0.0.0:9000) -> 9000
    ├─🔩 templates/local/monk-airbyte/airbyte-bootloader
    │  └─📦 8cee2a374dab7ad0a70196bf9bc9e425--airbyte-bootloader-bootloader
    │     └─🧩 airbyte/bootloader:0.40.18
    └─🔩 templates/local/monk-airbyte/airbyte-db
       └─📦 bc636812ee12dd23b5d5100f9983151f-cal-monk-airbyte-airbyte-db-db
          └─🧩 airbyte/db:0.40.18

💡 You can inspect and manage your above stack with these commands:
	monk logs (-f) monk-airbyte/stack - Inspect logs
	monk shell     monk-airbyte/stack - Connect to the container's shell
	monk do        monk-airbyte/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```
## Check web gui

`http://16.16.26.126/`



## Variables
The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| airbyte_version                |Airbyte version, Default: 0.40.18 	               |
| airbyte_config_database_password                    | Airbyte config database password, Default: '' 	               |
| airbyte_config_database_user                    | Airbyte config database user, Default: '' 	               |
| airbyte_config_database_url                    | Airbyte config database url, Default: '' 	               |
| airbyte_database_password                    | Airbyte database password, Default: monk 	               |
| airbyte_database_migration                    | Airbyte database migration, Default: true 	               |
| airbyte_trackings_strategy                    | Airbyte tracking strategy, Default: segment 	               |


## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```

