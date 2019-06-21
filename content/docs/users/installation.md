# Installing emrys for users

## Requirements
User subcommands have been tested with ubuntu 16.04 and macOS. There are no additional software dependencies for users, simply install the [CLI](/docs/installation#downloading-installing-emrys).

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

## Sending & receiving payments
Emrys payments are powered by [Stripe](https://stripe.com). Visit your [account](https://www.emrys.io/account) page to securely provide payment details required for using the network.

## Updating emrys

    # sudo may be required, depending on the permissions & ownership 
    # of where you installed the executable
    $ emrys update
