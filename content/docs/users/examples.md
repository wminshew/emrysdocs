# Example projects

Please note running these projects is not free (though the expected cost is ~< $0.02, subject to network demand)

## Basic

    // TODO: host on emrys
    $ curl -O https://www.emrys.io/download/basic-example.tar.gz
    $ tar -C ~/emrys-example -xzf basic-example.tar.gz
    $ cd ~/emrys-example/basic-example

    $ cat .emrys.yaml
    // TODO: output

    $ sudo emrys login
    Email: example@domain.com
    Password:

    $ sudo emrys run
    // TODO: expected output

    $ cd ~
    $ rm -r ~/emrys-example

## Advanced

The advanced example is not any more complex to complete, but includes a data set and a script to remotely train a model and return the final weights.

    // TODO: host on emrys
    $ curl -O https://www.emrys.io/download/advanced-example.tar.gz
    $ tar -C ~/emrys-example -xzf advanced-example.tar.gz
    $ cd ~/emrys-example/advanced-example

    $ cat .emrys.yaml
    // TODO: output

    $ sudo emrys login
    Email: example@domain.com
    Password:

    $ sudo emrys run // TODO: expected time to complete
    // TODO: expected output

    $ cat output/xxx
    // TODO: expected output

    $ cd ~
    $ rm -r ~/emrys-example
