# Using emrys

## Login

    emrys login

## Running jobs

Once a [configuration](/docs/users/config) file is in place, the user can dispatch jobs with the following command:

    emrys run

When convenient, flags will override configuration settings.

    ### use a different python script for execution
    emrys run --main test/numpy/other-main.py

## Running jupyter notebooks

Once a configuration file is in place, the user can access a remote jupyter kernel with the following command:

    ### launch with a blank notebook
    emrys notebook

    ### load a specific .ipynb notebook
    emrys notebook --main notebook.ipynb

Once the job is successfully auctioned and the kernel running, a jupyter token will be logged to the console for pasting into your browser.

## Where can I find real examples of running jobs & notebook?

[Here](/docs/users/examples)!

## How does it work?

Emrys run does ~4 things:

1. uploads a python script, conda environment, and pip requirements to the server with which a docker image is built
2. syncs the data set, if it exists locally, to the server
3. auctions the job's execution to supplier's meeting the user's hardware requirements
4. streams output logs back to the user & downloads anything the python script saved in ./output/

## Limitations

Please note when syncing your data set locally to emrys there is currently a maximum data set size of 10gb per project.
This limit is easily circumvented by downloading your data directly from your python script or notebook (but remember to request sufficient disk 
space in your config!)
