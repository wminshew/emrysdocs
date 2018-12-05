# Using emrys

## Login

    sudo emrys login

## Configuration

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys run:

    user:
      ## required
			# name of project
      project: "numpy-test"

			# path to pip requirements.txt
      requirements: "test/numpy/requirements.txt"

			# path to main python script for execution
      main: "test/numpy/main.py"

			# path to output folder
      output: "test/numpy/output"


      ## optional
			# path to data directory
      data: "test/numpy/data"

			# Minimum acceptable gpu, ranked here: https://github.com/wminshew/emrys/blob/master/pkg/job/ValidGPU.go
			# default: k80
			gpu: gtx 1080 ti

			# Minimum acceptable amount of supplier RAM
			# default: 8gb
			ram: 4gb

			# Minimum acceptable amount of supplier disk space
			# default: 25gb
			disk: 10gb

			# Minimum acceptable supplier gpu pci-e lanes
			# default: 8x
			pcie: 16x

## Running jobs

Once a configuration file is in place, the user can dispatch jobs with the following command:

    sudo emrys run

When convenient, flags will override configuration settings.

    # use a different python script for execution
    sudo emrys run --main test/numpy/other-main.py

## How does it work?

Emrys run does ~4 things:

1. uploads a python script and requirements to the server with which a docker image is built
2. syncs the data set, if it exists locally, to the server
3. auctions the job's execution to supplier's meeting the user's hardware requirements
4. streams output logs back to the user & downloads anything the python script saved in ./output/

## Limitations

Please note there is currently a maximum data set size of 10gb per project. Please email [support](mailto:support@emrys.io) to request a larger limit.
