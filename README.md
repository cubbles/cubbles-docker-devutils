# cubbles-docker-devutils
A set of utils, supporting core-developers to control a local docker-vm.

### Usage
1. Clone the Repo
2. Open your git-bash and `cd` into the root directory
  
  
  Basically you need to provide a .conf -file (`etc/xyz.conf`) AND 1..n commands (`lib/command-file.sh`)

    # Usage instructions
    $ ./bin/run.sh
    
    # Example1:
    $ ./bin/run.sh etc/base-local.conf lib/_docker-ps.sh
    
### Configuration
A default configuration is provides at "`etc/default/default.conf`".
Additionally some custom configuration files are prepared:

* `base-devbase.conf`: This is for developers of the Base itself. It provides configuration options to mount a local directory into the docker-vm.
* `base-local.conf`: Use this to setup and run a Cubbles Base locally. The configuration provides a Base -version (`CUBX_ENV_BASE_TAG`) the `setup` command is allowed to run.
* `sphinx.conf`: This is for developers of the Cubbles documentation published at <https://cubbles.readthedocs.io>.  It provides configuration options to mount a local directory into the docker-vm.
 