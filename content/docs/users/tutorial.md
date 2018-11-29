# Using emrys

## Login

    sudo emrys login

## Configuration

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys run:

    user:
      # required
      project: "numpy-test"
      requirements: "test/numpy/requirements.txt"
      main: "test/numpy/main.py"
      output: "test/numpy/output"

      # optional
      data: "test/numpy/data"

## Running jobs

Once a configuration file is in place, the user can dispatch jobs with the following command:

    sudo emrys run

When convenient, flags will override configuration settings.

    # use a different python script for execution
    sudo emrys run --main test/numpy/other-main.py

## Limitations

Please note there is currently a maximum data set size of 10gb per project. Please email [support](mailto:support@emrys.io) to request a larger limit.
