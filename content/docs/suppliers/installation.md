# Installing emrys for suppliers

## Requirements
Supplier / miner subcommands have only been tested with ubuntu 16.04, 18.04.

[Nvidia drivers](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa), 418 or newer


    ### uninstall any existing old drivers
    $ sudo apt-get purge nvidia*

    ### install nvidia drivers 418 (or higher)
    $ sudo add-apt-repository ppa:graphics-drivers
    $ sudo apt-get update
    $ sudo apt-get install -y nvidia-graphics-drivers-418
    ### depending on your OS, might be nvidia-driver-418 or simply nvidia-418
    ### can use nvidia-headless-418 nvidia-utils-418 if running headless, but if so make sure your GPUs are cooled properly!

    ### reboot
    $ sudo reboot

    ### verify the installation
    $ nvidia-smi


[Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/), v19.03 or newer
    
    ### uninstall any existing old versions (must run at least docker 19.03)
    $ sudo apt-get remove docker docker-engine docker.io containerd runc

    ### install docker
    $ sudo apt-get update
    $ sudo apt-get install -y \
       apt-transport-https \
       ca-certificates \
       curl \
       gnupg-agent \
       software-properties-common
        
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
       sudo apt-key add -
    ### verify you have the key with fingerprint 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
    $ sudo apt-key fingerprint 0EBFCD88
    $ sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

    $ sudo apt-get update
    $ sudo apt-get install -y docker-ce docker-ce-cli containerd.io

    ### verify the installation
    $ sudo docker run hello-world

    ### install nvidia-container-toolkit to add gpu support
    $ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    $ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
    $ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    $ sudo apt-get update
    $ sudo apt-get install -y nvidia-container-toolkit
    $ sudo systemctl restart docker

    ### verify the installation
    $ sudo docker run --gpus all nvidia/cuda nvidia-smi


<br>
Add [user re-mapping for security](https://docs.docker.com/engine/security/userns-remap/). All containers are executed as unprivileged users with all linux capabilities dropped and the [no-new-privileges](https://www.projectatomic.io/blog/2016/03/no-new-privs-docker/) security flag enabled. In the unlikely event a process were to escalate itself to privileged within the container and then escape to host, docker user re-mapping means the process would still be unprivileged on host.

    ### manually add "userns-remap": "default" to /etc/docker/daemon.json
    ### After, it should look like:
    $ sudo cat /etc/docker/daemon.json
    {
      "userns-remap": "default"
    }

    ### restart dockerd for the change to take effect
    $ sudo systemctl restart docker

    ### verify the change; depending on your docker privileges, may require sudo
    $ docker info | grep userns


<br>
Add [GPU cooling](https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Set_fan_speed_at_login). GPUs heat up quickly when running at high utilization. Settings your GPUs fan control state to manual
allows emrys to ramp up your fan appropriately during & between jobs. Keeping your cards
relatively cool reduces wear and tear.

    ### allows user to adjust gpu fan speed
    $ sudo nvidia-xconfig --enable-all-gpus
    $ sudo nvidia-xconfig --cool-bits=4

    ### reboot
    $ sudo reboot

    ### test
    $ nvidia-settings -a GPUFanControlState=1
    $ nvidia-settings -a GPUTargetFanSpeed=25


## Downloading & installing emrys

The following scripts require root privileges to install emrys into /usr/local/bin. If you prefer to avoid 
using sudo, simply install the executable into a different folder that doesn't require root (say ~/bin - 
but don't forget to add it to $PATH!)

### Linux

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_linux.tar.gz | \
       sudo tar -C /usr/local/bin -xzf -

### MacOS

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_darwin.tar.gz | \
       sudo tar -C /usr/local/bin -xzf -

### Test the installation

    $ emrys --help

## Receiving payments
Emrys payments are powered by [Stripe](https://stripe.com). Visit your [account](https://www.emrys.io/account) page to securely provide bank account details required for payouts from supplying the network.

## Updating emrys

    ### sudo may be required, depending on the permissions & ownership 
    ### of where you installed the executable
    $ emrys update

## Configuring emrys

Before executing the miner subcommand, please make sure to [configure emrys](/docs/suppliers/config).
