# Configuring emrys for suppliers

For convenience, suppliers should store their settings in a configuation file. Emrys will look for .emrys.yaml in the prioritized order: current directory, $HOME/.config/emrys, and $HOME/. Toml and json formats are also accepted.

Example .emrys.yaml:

    # which devices to rent out on the network (mapped to nvidia-smi);
    # if left empty, emrys will run on all discoverable devices
    devices: 0 1

    # minimum $/hr rate each device will accept for jobs;
    # may include either one number (used for all cards),
    # or n numbers where n is the number of running devices
    bid-rates: 0.2 0.3

    # NOTE: if included, must use the '$DEVICE' flag
    mining-command: [command] --cuda_devices $DEVICE --server [server]
      --user [user] --port [port]
