
# <img src="https://avatars3.githubusercontent.com/u/34816118?s=200&v=4" data-canonical-src="hhttps://avatars3.githubusercontent.com/u/34816118?s=200&v=4" width="40" height="40" /> Snark AI

## Basic Usage
**Step 1**. Install snark through pip3
```
$ pip3 install snark --user
```

**Step 2**. Go to [lab.snark.ai](https://lab.snark.ai) to sign up. Sign in through the CLI
```
$ snark login
```
It will ask you for username and password that you registered on the website.

**Step 3**. You can start your pod by 
```
$ snark start --pod_id  kagglepod  --pod_type tensorflow  -g 2
```
tensorflow pod has TF version 1.8.0 with cuda 9 , cudnn 7 in python3 and keras frontend. -g 2 means 2 GPUs.  You will directly login to your pod.

Other available pod types: 
 - **pytorch**: pytorch version 0.4.0 with cuda 9, cudnn 7 in python 3. Caffe2 is also installed in the pod
 - **mxnet**: mxnet version 1.0.0 with cuda 9, cudnn 7 in python 3.
 - **theano**: theano version 0.8.2 with cuda 8, cudnn 5 in python 3
 - **caffe** : caffe version 1.0 with cuda 8, cudnn 6 in python 3

**Step 4**. Stop the pod by
```
$ snark stop --pod_id kagglepod
```


Use `snark ls` to list your active pods.

## File Transfer
You can push/pull data to the pod by snark pull and snark push. 


### Download Files
```bash
$ snark pull --help
Usage: snark pull [OPTIONS]

  Transfer file from the pod to the localhost

Options:
  -p, --pod_id TEXT       Pod ID
  -r, --remote_path TEXT  Path to file on the Pod.
  -l, --local_path TEXT   Path to file on local machine.
  --help                  Show this message and exit.
```

### Upload Files
```bash
$ snark push --help
Usage: snark push [OPTIONS]

  Transfer file to the pod

Options:
  -p, --pod_id TEXT       Pod ID
  -l, --local_path TEXT   Path to file on local machine.
  -r, --remote_path TEXT  Path to file on the Pod.
  --help                  Show this message and exit.
```
Note: if you want use `~'` or `\*` when specifying remote file path, please take them in quotes. Eg:
```
snark push --pod_id kaggle_pod -r "~/test.txt" -l test.txt
```

## Persistent Storage
There's no Persistent storage on the pod -- your files will be gone when you stop your pod. Before you stop the pod, please push your code to `git` and save other files through `snark pull`. 

If you would like to create a persistant pod, shoot us an email at *support@snark.ai*. 

Common datasets from Kaggle competitions and more are accessible (read only) at `/datasets`. If there's a dataset you would like to add/request, let us know! *support@snark.ai*

## Usage Monitor
Login to [lab.snark.ai](https://lab.snark.ai) to check the GPU hour used and credit left.

## GPU spec and Pricing 
Right now we are providing NVIDIA P106 GPUs. For machine learning, these GPUs are slighlty faster than NVIDIA K80. We're currently working on providing 1080's.

You'll be billed **9.5 cents** per hour of GPU time, which is much cheaper than anywhere else.

Our new custormes get **1.5 hours** of free GPU time to play around!
