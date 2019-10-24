---
title: Docs
type: docs
---

# Documentation

Welcome to emrys! Here we'll teach you how to get started. 

# Installing emrys

We support Linux and MacOS. 

## Linux

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_linux.tar.gz -O 
    $ tar -C /usr/local/bin -xzf emrys_{{< version >}}_linux.tar.gz 
    
    ### may need sudo, depending on permissions

## MacOS

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_darwin.tar.gz -O 
    $ tar -C /usr/local/bin -xzf emrys_{{< version >}}_darwin.tar.gz 
    
    ### may need sudo, depending on permissions

# Using emrys

## Login

    $ emrys login

## Add credit card
We require a credit card to use the network.  You will not be charged until after your trial ends and you run out of credits.  Visit your [account](https://www.emrys.io/account) page to securely provide payment details.

## Run an example

Here's an example jupyter notebook for you to try.  

    $ curl https://storage.googleapis.com/emrys-public/tutorials/advanced-notebook-example.tar.gz | tar -xzf -
    $ cd advanced-notebook
    $ emrys notebook
    
    ### click on the 127.0.0.1 link to open the jupyter notebook in your browser (or copy/paste)

Notebook kindly borrowed from [jovian](https://medium.com/dsnet/training-deep-neural-networks-on-a-gpu-with-pytorch-11079d89805).

## Run your own notebook

To run your own notebook, you'll need to [create a configuration file ](/#configuring-emrys) first. 

Once a configuration file is in place, the user can access a remote jupyter kernel with the following command:

    ### launch with a blank notebook
    $ emrys notebook

    ### load a specific .ipynb notebook
    $ emrys notebook --main notebook.ipynb

Once the job is successfully running, a jupyter token will be logged to the console for pasting into your browser.

### Where can I find real examples of running notebooks?

[Here](/docs/users/examples)!

# Advanced

## How does emrys work?

Emrys run does ~4 things:

1. uploads a python script, conda environment, and pip requirements to the server with which a docker image is built
2. syncs the data set, if it exists locally, to the server
3. auctions the job's execution to suppliers meeting the user's hardware requirements
4. streams output logs back to the user & downloads anything the python script saved in ./output/

## Limitations

Please note when syncing your data set locally to emrys there is currently a maximum data set size of 10gb per project.
This limit is easily circumvented by downloading your data directly from your python script or notebook (but remember to request sufficient disk 
space in your config!)

## Updating emrys

    ### sudo may be required, depending on the permissions & ownership 
    ### of where the emrys binary is located
    $ emrys update
    
## Configuring emrys

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys notebook:

    user:
      ## required
      ### name of project
      project: "numpy-test"

      ### path to output folder
      output: "test/output"

      ### path to conda environment.yml
      conda-env: "test/environment.yml"

      ### path to pip requirements.txt
      pip-reqs: "test/requirements.txt"

      ### path to data directory
      data: "test/data"

      ### minimum acceptable amount of RAM
      ### default: 8gb
      ram: 4gb

      ### minimum acceptable amount of disk space
      ### default: 25gb
      disk: 10gb



