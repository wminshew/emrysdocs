---
title: Docs
type: docs
---

# Documentation

Welcome to emrys! Here we'll teach you how to get started. 

# Install emrys

We support Linux and MacOS. 

## Linux

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_linux.tar.gz -O 
    $ tar -C /usr/local/bin -xzf emrys_{{< version >}}_linux.tar.gz 
    
    ### may need sudo, depending on permissions

## MacOS

    $ curl https://storage.googleapis.com/emrys-public/clients/emrys_{{< version >}}_darwin.tar.gz -O 
    $ tar -C /usr/local/bin -xzf emrys_{{< version >}}_darwin.tar.gz 
    
    ### may need sudo, depending on permissions

# Use emrys

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

## Where can I find real examples of running notebooks?

[Here](/docs/users/examples)!

# Advanced

## How does emrys work?

Emrys does 4 things:

1. syncs the data set, if one exists locally
2. builds a docker image with your python script (or notebook), conda environment, and pip requirements
3. auctions the job to suppliers meeting your hardware requirements
4. streams output back to the user

## Limitations

Please note when syncing a local data set to emrys there is a maximum size of 10gb per project.
This may be circumvented by downloading your data directly from your python script or notebook (remember to specify sufficient disk 
space!)

## Update emrys

    $ emrys update

    ### may need sudo, depending on permissions
    
## Configure emrys

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys notebook:

    user:
      ## required

      ### name of project
      project: "test"

      ### path to output folder
      output: "output"


      ## optional

      ### path to conda environment.yml
      conda-env: "environment.yml"

      ### path to pip requirements.txt
      pip-reqs: "requirements.txt"

      ### path to data directory
      data: "data"

      ### minimum acceptable amount of RAM
      ### default: 8gb
      ram: 4gb

      ### minimum acceptable amount of disk space
      ### default: 25gb
      disk: 10gb


