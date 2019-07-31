# Configuring emrys for users

For convenience, users should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys run:

    user:
      ## required
      ### name of project
      project: "numpy-test"

      ### path to main python script for execution
      main: "test/numpy/main.py"

      ### path to output folder
      output: "test/numpy/output"

      ## optional
      ### path to conda environment.yml
      conda-env: "test/numpy/environment.yml"

      ### path to pip requirements.txt
      pip-reqs: "test/numpy/requirements.txt"

      ### path to data directory
      data: "test/numpy/data"

      ### minimum acceptable gpu
      ### rankings: https://github.com/wminshew/emrys/blob/master/pkg/job/ValidGPU.go
      ### default: k80
      gpu: gtx 1080

      ### minimum acceptable amount of supplier RAM
      ### default: 8gb
      ram: 4gb

      ### minimum acceptable amount of supplier disk space
      ### default: 25gb
      disk: 10gb

      ### minimum acceptable supplier gpu pci-e lanes
      ### default: 8x
      pcie: 4x

Example .emrys.yaml for executing emrys notebook:

    user:
      ## required
      ### name of project
      project: "numpy-test"

      ### path to output folder
      output: "test/numpy/output"

      ## optional
      ### path to jupyter notebook
      main: "test/numpy/main.ipynb"

      ### path to conda environment.yml
      conda-env: "test/numpy/environment.yml"

      ### path to pip requirements.txt
      pip-reqs: "test/numpy/requirements.txt"

      ### path to data directory
      data: "test/numpy/data"

      ### minimum acceptable gpu
      ### rankings: https://github.com/wminshew/emrys/blob/master/pkg/job/ValidGPU.go
      ### default: k80
      gpu: gtx 1080

      ### minimum acceptable amount of supplier RAM
      ### default: 8gb
      ram: 4gb

      ### minimum acceptable amount of supplier disk space
      ### default: 25gb
      disk: 10gb

      ### minimum acceptable supplier gpu pci-e lanes
      ### default: 8x
      pcie: 4x
