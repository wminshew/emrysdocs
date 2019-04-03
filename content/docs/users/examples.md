# Example projects

Please note running these projects is not free (though the expected cost is ~< $0.02, subject to network demand). 
Even if you have credits, you must add a valid card to your [account](https://www.emrys.io/account) (powered by [Stripe](https://stripe.com)).

## Basic

	$ curl -O https://storage.googleapis.com/emrys-public/tutorials/basic-example.tar.gz
	$ tar -xzf basic-example.tar.gz
	$ cd basic-example

	# if not already logged in
	$ sudo emrys login
	Email: example@domain.com
	Password:

	$ sudo emrys run
	2018/12/06 12:42:23 Sending job requirements...
	2018/12/06 12:42:23 Beginning job 6898781b-5c9d-40a5-b070-722fdca88138...
	2018/12/06 12:42:23 Data: syncing...
	2018/12/06 12:42:23 Data: no directory provided.
	2018/12/06 12:42:23 Image: packing request...
	2018/12/06 12:42:23 Image: building...
	2018/12/06 12:42:25 Data: 0 file(s) to upload
	2018/12/06 12:42:25 Data: synced!
	2018/12/06 12:42:49 Image: built!
	2018/12/06 12:42:49 Searching for cheapest compute meeting your requirements...
	2018/12/06 12:42:56 Miner selected!
	2018/12/06 12:42:56 Executing job 6898781b-5c9d-40a5-b070-722fdca88138...
	2018/12/06 12:42:56 Output log: streaming... (may take a minute to begin)
	[[ 0  1  2  3  4 ]
	 [ 5  6  7  8  9 ]
	 [10 11 12 13 14]]
	<class 'numpy.ndarray'>
	2018/12/06 12:43:02 Output data: downloading...
	2018/12/06 12:43:02 Complete!

## Advanced

The advanced example is not any more complex to complete, but includes a data set and a script to remotely train a model and return the final weights.

	$ curl -O https://storage.googleapis.com/emrys-public/tutorials/advanced-example.tar.gz
	$ tar -xzf advanced-example.tar.gz
	$ cd advanced-example
	
	# if not already logged in
	$ sudo emrys login
	Email: example@domain.com
	Password:

	$ sudo emrys run
	# you can also download the data set remotely (vs syncing from local) by running:
	# sudo emrys run --main main-gpu-dl.py --data ""
	2018/12/06 17:48:42 Sending job requirements...
	2018/12/06 17:48:42 Beginning job ce87fc77-65a8-47bb-a153-91b300eadc2f...
	2018/12/06 17:48:42 Data: syncing...
	2018/12/06 17:48:42 Image: packing request...
	2018/12/06 17:48:42 Image: building...
	2018/12/06 17:48:42 Data: 6 file(s) to upload
	2018/12/06 17:48:42 Data: uploading: raw/train-images-idx3-ubyte
	2018/12/06 17:48:42 Data: uploading: raw/train-labels-idx1-ubyte
	2018/12/06 17:48:42 Data: uploading: processed/test.pt
	2018/12/06 17:48:42 Data: uploading: processed/training.pt
	2018/12/06 17:48:42 Data: uploading: raw/t10k-images-idx3-ubyte
	2018/12/06 17:48:43 Data: uploading: raw/t10k-labels-idx1-ubyte
	2018/12/06 17:48:43 Data: uploaded raw/train-labels-idx1-ubyte
	2018/12/06 17:48:43 Data: uploaded raw/t10k-labels-idx1-ubyte
	2018/12/06 17:48:43 Data: uploaded raw/t10k-images-idx3-ubyte
	2018/12/06 17:48:43 Data: uploaded processed/test.pt
	2018/12/06 17:48:45 Data: uploaded processed/training.pt
	2018/12/06 17:48:45 Data: uploaded raw/train-images-idx3-ubyte
	2018/12/06 17:48:45 Data: synced!
	2018/12/06 17:51:08 Image: built!
	2018/12/06 17:51:08 Searching for cheapest compute meeting your requirements...
	2018/12/06 17:51:16 Miner selected!
	2018/12/06 17:51:16 Executing job ce87fc77-65a8-47bb-a153-91b300eadc2f...
	2018/12/06 17:51:16 Output log: streaming... (may take a minute to begin)
	Epoch [1/1], Iter [100/600] Loss: 0.1879
	Epoch [1/1], Iter [200/600] Loss: 0.1063
	Epoch [1/1], Iter [300/600] Loss: 0.0717
	Epoch [1/1], Iter [400/600] Loss: 0.0466
	Epoch [1/1], Iter [500/600] Loss: 0.0445
	Epoch [1/1], Iter [600/600] Loss: 0.1142
	Test Accuracy of the model on the 10000 test images: 98 %
	2018/12/06 17:52:13 Output data: downloading...
	2018/12/06 17:52:13 Complete!

	$ tree output/
	output
	└── ce87fc77-65a8-47bb-a153-91b300eadc2f
	  ├── data
	  │   └── cnn.pkl
	  └── log
