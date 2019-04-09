# Configuring emrys for suppliers

For convenience, suppliers should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml for executing emrys mine:

    miner:
      ## required
      # minimum $/hr rate each device will accept for jobs;
      # may include either one number (used for all cards),
      # or n numbers where n is the number of running devices
      bid-rates: 0.2 0.21

      ## optional
      # which devices to rent out on the network (mapped to nvidia-smi);
      # defaults to all discoverable devices
      devices: 0 1

      # how much RAM to allocate per device per job
      # default: 8gb
      ram: 4gb

      # how much disk space to allocate per device per job
      # default: 25gb
      disk: 50gb

      # a command to execute per device during idle time (between
      # emrys jobs)
      # NOTE: if included, MUST use the '$DEVICE' flag, as shown below
      mining-command: [command] --cuda_devices $DEVICE --server [server]
        --user [user] --port [port]
