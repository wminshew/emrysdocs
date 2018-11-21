# Using emrys

## Login

    emrys login

## Configuration

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml:

    # required
    project: "numpy-test"
    requirements: "test/numpy/requirements.txt"
    main: "test/numpy/main.py"
    output: "test/numpy/output"

    # optional
    data: "test/numpy/data"

## Running jobs

Once a configuration file is in place, the user can dispatch jobs with the following command:

    emrys run

When convenient, flags will override configuration settings.

    # use a different python script for execution
    emrys run --main test/numpy/other-main.py
