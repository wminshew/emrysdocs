# Installing emrys

## Requirements
**General**<br>
Ubuntu 16.04. May work with other versions or OSes, but hasn't been tested. Experiment at your own risk.

**User**<br>
None

**Supplier**<br>
[Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

    # Uninstall old versions
    $ sudo apt-get remove docker docker-engine docker.io

    $ sudo apt-get update
    $ sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        software-properties-common
        
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    $ sudo apt-key fingerprint 0EBFCD88
    $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

    $ sudo apt-get update
    $ sudo apt-get install docker-ce

[Nvidia-Docker](https://github.com/NVIDIA/nvidia-docker)

    # Add the package repositories
    $ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
      sudo apt-key add -
    $ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    $ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
      sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    $ sudo apt-get update

    # Install nvidia-docker2 and reload the Docker daemon configuration
    $ sudo apt-get install -y nvidia-docker2
    $ sudo systemctl restart docker.service

## Downloading

### Curl

    curl -0 https://www.emrys.io/download/emrys_{{< version >}}.tar.gz
    tar -C /usr/local -xzf emrys_{{< version >}}.tar.gz

    # test the installation
    emrys --help

## Best Practices

**User**<br>
None

**Supplier**<br>
To further isolate containers from your host machine, we suggest taking the following pre-cautions. While we believe the security settings enabled by default are sufficient, when it comes to security the more layers the better.

Enable [user re-mapping to docker](https://docs.docker.com/engine/security/userns-remap/). All containers are executed as unprivileged users with all linux capabilities dropped and the [no-new-privileges](https://www.projectatomic.io/blog/2016/03/no-new-privs-docker/) security flag enabled. In the unlikely event the process were to escalate itself to a privileged user within the container, the docker user re-mapping means the process still wouldn't be privileged on your host machine.

    # add "userns-remap": "default" to /etc/docker/daemon.json, then restart dockerd
    # should look like: 
    $ sudo cat /etc/docker/daemon.json
    {
        "userns-remap": "default"
    }
    $ sudo systemctl restart docker.service

Run emrys inside [LXD](https://help.ubuntu.com/lts/serverguide/lxd.html), a light-weight container hypervisor. In the unlikely event a process were able to escape from the container, LXD would add an extra buffer to break through before reaching the host machine.

// TODO
