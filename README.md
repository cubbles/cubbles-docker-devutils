# base-remote-control
Purpose: Setup and control a Cubbles-Base ... locally or on a remote host. 

## Usage
1. Clone the Repo
2. Open your git-bash and `cd` into the root directory
  
  
Basically you need to provide a .conf -file (`etc/xyz.conf`) AND 1..n commands (`lib/.../command-file.sh`)

```bash
    # Usage instructions
    $ ./bin/run.sh
    
    # Example:
    $ ./bin/run.sh etc/base-local.conf lib/base/setup.sh
```
    
## Configuration
The default configuration is provided at "`etc/default/default.conf`".
Put your custom configurations into the "`etc`" directory. Any additional `.conf` files there are ignored by git (by default).  

### Remote Control Configuration
The Remote Control (esp. the commands within the `/lib` folder) are configured using `/etc/*.conf` files. The config defines e.g. the host the command will be executed on (`DOCKER_VBOX` or `DOCKER_REMOTE_HOST_IP`)

Some configuration files for a local setup are prepared at `etc/`:

* `base-local.conf`: Use this to setup and run a Cubbles Base locally using `docker-machine` and `virtual box`.
* `base-local-ssh.conf`: The same as `base-local.conf` but to exemplify the interaction via ssh only.

### Base Configuration
The `etc/*.conf` file refers to a *local* and a *host* -config folder:

```bash
ENV_LOCAL_CONFIG_FOLDERS="opt/host-resources/cubbles-base-local"
ENV_HOST_CONFIG_FOLDER="/mnt/sda1/tmp/base-config-local"
```

* `ENV_LOCAL_CONFIG_FOLDERS`: The _local_ folder to manage additional resource for the Base instance a runtime. 
    * The folder may contain any number of resources, but is expected to contain a `docker-compose-custom.yml` file. 
* `ENV_HOST_CONFIG_FOLDER`: The _host_ folder all the (local) resources will be transferred to. 
    * The folder will be created (and updated) automatically, when running the `lib/base/setup.sh` command. 
    * Take care your `DOCKER_REMOTE_HOST_USER` has the permissions to create this folder on the host.

Want to setup some individual configs? Just copy one of the existing files, adapt it to your needs and use it. 

## Known Issues
Known Issues are managed in [JIRA](https://cubbles.atlassian.net/issues/?filter=10200). Your are welcome to raise a bug report or propose useful improvements.