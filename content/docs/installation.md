# Installing emrys

## Requirements
**General**<br>
Ubuntu 16.04. May work with other versions or OSes, but hasn't been tested. Experiment at your own risk.

**User**<br>
None

**Supplier**<br>
[Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
    # Uninstall old versions
    $ sudo apt remove docker docker-engine docker.io

    $ sudo apt update
    $ sudo apt install \
       apt-transport-https \
       ca-certificates \
       curl \
       software-properties-common
        
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
       sudo apt-key add -
    $ sudo apt-key fingerprint 0EBFCD88
    $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

    $ sudo apt update
    $ sudo apt install -y docker-ce

<br>
[Nvidia-Docker](https://github.com/NVIDIA/nvidia-docker)

    # Add the package repositories
    $ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
       sudo apt-key add -
    $ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    $ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
       sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    $ sudo apt update

    # Install nvidia-docker2 and reload the Docker daemon configuration
    $ sudo apt install -y nvidia-docker2
    $ sudo systemctl restart docker.service

<br>
Add [user re-mapping for security](https://docs.docker.com/engine/security/userns-remap/). All containers are executed as unprivileged users with all linux capabilities dropped and the [no-new-privileges](https://www.projectatomic.io/blog/2016/03/no-new-privs-docker/) security flag enabled. In the unlikely event the process were to escalate itself to a privileged user within the container, the docker user re-mapping means the process is still unprivileged on your host machine.

    # manually add "userns-remap": "default" to /etc/docker/daemon.json
    # After, it should look like: 
    $ sudo cat /etc/docker/daemon.json
    {
      "userns-remap": "default",
      "runtimes": {
        "nvidia": {
          "path": "nvidia-container-runtime",
          "runtimeArgs": []
        }
      }
    }

    # restart dockerd for the changes to take effect
    $ sudo systemctl restart docker.service


<br>
[GPU cooling](https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Set_fan_speed_at_login)

    # allows user to adjust gpu fan speed
    $ sudo nvidia-xconfig -a --enable-all-gpus
    $ sudo nvidia-xconfig -a --cool-bits=24

    # must reboot

    # test
    $ nvidia-settings -a GPUFanControlState=1
    $ nvidia-settings -a GPUTargetFanSpeed=25

GPUs heat up quickly when running at high utilization. Settings your GPUs fan control state to manual
allows emrys to ramp up your fan appropriately during & between jobs. Keeping your cards
relatively cool reduces wear and tear.

## Downloading & installing emrys

    $ curl -O https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}.tar.gz | \
       sudo tar -C /usr/local/bin -xzf -

    # test the installation
    $ emrys --help

  # enable docker user re-mapping

## Sending & receiving payments
Emrys payments are powered by [Stripe](https://stripe.com). Visit your [account](https://www.emrys.io/account) page to securely provide card and/or bank account details required for using & supplying the network respectively.

## Updating emrys

    $ sudo emrys update
