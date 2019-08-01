# Example projects

Please note running these projects is not free (though the expected cost is $0.01-$0.02, subject to network demand). 
Even if you have credits, to access the network you must add a valid 
card to your [account](https://www.emrys.io/account) (powered by [Stripe](https://stripe.com)).

## Basic notebook

    $ curl -O https://storage.googleapis.com/emrys-public/tutorials/basic-notebook-example.tar.gz | tar -xzf -
    $ cd basic-notebook

    ### if not already logged in
    $ emrys login
    Email: example@domain.com
    Password:

    $ emrys notebook
    2019/07/31 00:54:46 Connecting to server...
    2019/07/31 00:54:53 Beginning job d492a8a2-eb3b-4b14-93d2-6e5ca5a6f037...
    2019/07/31 00:54:53 Data: syncing...
    2019/07/31 00:54:53 Data: no directory provided.
    2019/07/31 00:54:53 Image: packing request...
    2019/07/31 00:54:53 Image: building...
    2019/07/31 00:54:54 Data: 0 file(s) to upload
    2019/07/31 00:54:54 Data: synced!
    2019/07/31 00:55:07 Image: built!
    2019/07/31 00:55:07 Searching for cheapest compute meeting your requirements...
    2019/07/31 00:55:11 Miner selected!
    2019/07/31 00:55:11 Executing notebook d492a8a2-eb3b-4b14-93d2-6e5ca5a6f037...
    2019/07/31 00:55:11 Output log: streaming... (may take a minute to begin)
    [I 07:55:50.547 NotebookApp] Writing notebook server cookie secret to /home/user/.local/share/jupyter/runtime/notebook_cookie_secret
    [I 07:55:50.717 NotebookApp] Serving notebooks from local directory: /home/user
    [I 07:55:50.717 NotebookApp] The Jupyter Notebook is running at:
    [I 07:55:50.717 NotebookApp] http://eba6b5ef02a0:8888/?token=f6c7544d15704ab3ac5e148340aa3fef22ee1892cd7348ac
    [I 07:55:50.717 NotebookApp]  or http://127.0.0.1:8888/?token=f6c7544d15704ab3ac5e148340aa3fef22ee1892cd7348ac
    [I 07:55:50.717 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
    [C 07:55:50.720 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-6-open.html
    Or copy and paste one of these URLs:
        http://eba6b5ef02a0:8888/?token=f6c7544d15704ab3ac5e148340aa3fef22ee1892cd7348ac
     or http://127.0.0.1:8888/?token=f6c7544d15704ab3ac5e148340aa3fef22ee1892cd7348ac

    ### click on the 127.0.0.1 link to open in your browser (or copy/paste)
    ### when done, press ctrl-c to end

    2019/07/31 00:55:53 Cancellation request received: please wait for notebook to successfully cancel
    2019/07/31 00:55:53 Warning: failure to successfully cancel notebook may result in undesirable charges
    2019/07/31 00:55:53 Canceling job d492a8a2-eb3b-4b14-93d2-6e5ca5a6f037...
    JOB CANCELED BY USER.
    2019/07/31 00:55:53 Job canceled
    2019/07/31 00:55:54 Output data: downloading...
    2019/07/31 00:55:54 Output data: downloaded!

## Basic run

    $ curl https://storage.googleapis.com/emrys-public/tutorials/basic-example.tar.gz | tar -xzf -
    $ cd basic

    ### if not already logged in
    $ emrys login
    Email: example@domain.com
    Password:

    $ emrys run
    2019/07/31 00:58:56 Connecting to server...
    2019/07/31 00:58:56 Beginning job ee4a8002-1d2c-427d-901f-3dd9f3dcb3d9...
    2019/07/31 00:58:56 Data: syncing...
    2019/07/31 00:58:56 Data: no directory provided.
    2019/07/31 00:58:56 Image: packing request...
    2019/07/31 00:58:56 Image: building...
    2019/07/31 00:58:57 Data: 0 file(s) to upload
    2019/07/31 00:58:57 Data: synced!
    2019/07/31 00:59:10 Image: built!
    2019/07/31 00:59:10 Searching for cheapest compute meeting your requirements...
    2019/07/31 00:59:14 Miner selected!
    2019/07/31 00:59:14 Executing job ee4a8002-1d2c-427d-901f-3dd9f3dcb3d9...
    2019/07/31 00:59:14 Output log: streaming... (may take a minute to begin)
    Collecting numpy (from -r requirements.txt (line 1))
      Downloading https://files.pythonhosted.org/packages/05/4b/55cfbfd3e5e85016eeef9f21c0ec809d978706a0d60b62cc28aeec8c792f/numpy-1.17.0-cp37-cp37m-manylinux1_x86_64.whl (20.3MB)

    Installing collected packages: numpy
    Successfully installed numpy-1.17.0
    [[ 0  1  2  3  4]
     [ 5  6  7  8  9]
     [10 11 12 13 14]]
    <class 'numpy.ndarray'>
    2019/07/31 00:59:31 Output data: downloading...
    2019/07/31 00:59:31 Output data: downloaded!
    2019/07/31 00:59:31 Complete!

## Advanced notebook

Notebook kindly borrowed from [jovian](https://medium.com/dsnet/training-deep-neural-networks-on-a-gpu-with-pytorch-11079d89805).

    $ curl https://storage.googleapis.com/emrys-public/tutorials/advanced-notebook-example.tar.gz | tar -xzf -
    $ cd advanced-notebook

    ### if not already logged in
    $ emrys login
    Email: example@domain.com
    Password:

    $ emrys notebook
    2019/07/31 00:43:14 Connecting to server...
    2019/07/31 00:43:17 Beginning job 6d08e19f-5b50-4b3f-a962-b8cd66790833...
    2019/07/31 00:43:17 Data: syncing...
    2019/07/31 00:43:17 Data: no directory provided.
    2019/07/31 00:43:17 Image: packing request...
    2019/07/31 00:43:17 Image: building...
    2019/07/31 00:43:19 Data: 0 file(s) to upload
    2019/07/31 00:43:19 Data: synced!
    2019/07/31 00:43:33 Image: built!
    2019/07/31 00:43:33 Searching for cheapest compute meeting your requirements...
    2019/07/31 00:43:37 Miner selected!
    2019/07/31 00:43:37 Executing notebook 6d08e19f-5b50-4b3f-a962-b8cd66790833...
    2019/07/31 00:43:37 Output log: streaming... (may take a minute to begin)
    Collecting package metadata (repodata.json): ...working... done
    Solving environment: ...working... done
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    [I 07:45:23.380 NotebookApp] Writing notebook server cookie secret to /home/user/.local/share/jupyter/runtime/notebook_cookie_secret
    [I 07:45:23.554 NotebookApp] Serving notebooks from local directory: /home/user
    [I 07:45:23.554 NotebookApp] The Jupyter Notebook is running at:
    [I 07:45:23.554 NotebookApp] http://(be4fe6c8740c or 127.0.0.1):8888/?token=39e27295259f52a38a2934f7f4c56528d1b438b9e3826cab
    [I 07:45:23.554 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
    [W 07:45:23.558 NotebookApp] No web browser found: could not locate runnable browser.
    [C 07:45:23.558 NotebookApp] 
    
    To access the notebook, open this file in a browser:
        file:///home/user/.local/share/jupyter/runtime/nbserver-6-open.html
    Or copy and paste one of these URLs:
        http://(be4fe6c8740c or 127.0.0.1):8888/?token=39e27295259f52a38a2934f7f4c56528d1b438b9e3826cab

    ### open up http://127.0.0.1:8888?token=[token] in your browser to access the notebook
    ### when done, press ctrl-c to end

## Advanced run

The advanced example is not any more complex to complete, but includes a data set and a script to remotely train a model and return the final weights.

    $ curl https://storage.googleapis.com/emrys-public/tutorials/advanced-example.tar.gz | tar -xzf -
    $ cd advanced
    
    ### if not already logged in
    $ emrys login
    Email: example@domain.com
    Password:

    $ emrys run
    ### you can also download the data set remotely (vs syncing from local) by running:
    ### emrys run --main main-gpu-dl.py --data ""
    2019/07/31 01:30:10 Connecting to server...
    2019/07/31 01:30:11 Beginning job 1cc5f9b6-45eb-44a7-8494-f2f4f28d2867...
    2019/07/31 01:30:11 Data: syncing...
    2019/07/31 01:30:11 Image: packing request...
    2019/07/31 01:30:11 Image: building...
    2019/07/31 01:30:11 Data: 0 file(s) to upload
    2019/07/31 01:30:11 Data: synced!
    2019/07/31 01:30:25 Image: built!
    2019/07/31 01:30:25 Searching for cheapest compute meeting your requirements...
    2019/07/31 01:30:29 Miner selected!
    2019/07/31 01:30:29 Executing job 1cc5f9b6-45eb-44a7-8494-f2f4f28d2867...
    2019/07/31 01:30:29 Output log: streaming... (may take a minute to begin)
    Collecting package metadata (repodata.json): ...working... done
    Solving environment: ...working... done
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    /entrypoint.sh: line 17: [: 10.0.1: binary operator expected
    Collecting numpy==1.14.2 (from -r requirements.txt (line 1))
      Downloading https://files.pythonhosted.org/packages/ea/31/991207e6234b46a1228be970735ead9d6f06a298917d6f718c5e32e835bb/numpy-1.14.2-cp35-cp35m-manylinux1_x86_64.whl (12.1MB)

    Collecting Pillow==5.1.0 (from -r requirements.txt (line 2))
      Downloading https://files.pythonhosted.org/packages/07/52/8e27b9c54cb70d379244771a58483928b3a02db3c657d466ed84eb18f22b/Pillow-5.1.0-cp35-cp35m-manylinux1_x86_64.whl (2.0MB)

    Collecting PyYAML==3.12 (from -r requirements.txt (line 3))
      Downloading https://files.pythonhosted.org/packages/4a/85/db5a2df477072b2902b0eb892feb37d88ac635d36245a72a6a69b23b383a/PyYAML-3.12.tar.gz (253kB)

    Collecting six==1.11.0 (from -r requirements.txt (line 4))
      Downloading https://files.pythonhosted.org/packages/67/4b/141a581104b1f6397bfa78ac9d43d8ad29a7ca43ea90a2d863fe3056e86a/six-1.11.0-py2.py3-none-any.whl
    Collecting torch==0.3.1 (from -r requirements.txt (line 5))
      Downloading https://files.pythonhosted.org/packages/e8/c5/0763a145e051ce7c84c128621693d1c5dfad5a42d551e8d79742261002e2/torch-0.3.1-cp35-cp35m-manylinux1_x86_64.whl (496.4MB)

    Collecting torchvision==0.2.0 (from -r requirements.txt (line 6))
      Downloading https://files.pythonhosted.org/packages/e9/c9/f4eb36734bffd36eb8095247d816cbe6aeca0a2b9218b78678288edfdb92/torchvision-0.2.0-py2.py3-none-any.whl (48kB)

    Installing collected packages: numpy, Pillow, PyYAML, six, torch, torchvision
      Running setup.py install for PyYAML ... done
    Successfully installed Pillow-5.1.0 PyYAML-3.12 numpy-1.14.2 six-1.11.0 torch-0.3.1 torchvision-0.2.0
    You are using pip version 10.0.1, however version 19.2.1 is available.
    You should consider upgrading via the 'pip install --upgrade pip' command.
    Epoch [1/1], Iter [100/600] Loss: 0.1293
    Epoch [1/1], Iter [200/600] Loss: 0.0461
    Epoch [1/1], Iter [300/600] Loss: 0.1245
    Epoch [1/1], Iter [400/600] Loss: 0.0686
    Epoch [1/1], Iter [500/600] Loss: 0.0514
    Epoch [1/1], Iter [600/600] Loss: 0.0693
    Test Accuracy of the model on the 10000 test images: 97 %
    2019/07/31 01:31:19 Output data: downloading...
    2019/07/31 01:31:19 Output data: downloaded!
    2019/07/31 01:31:19 Complete!

    ### check the output
    $ tree output/
    output
    └── 1cc5f9b6-45eb-44a7-8494-f2f4f28d2867
      ├── data
      │   └── cnn.pkl
      └── log
