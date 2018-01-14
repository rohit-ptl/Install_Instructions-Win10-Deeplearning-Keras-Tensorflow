# Install instructions for TensorFlow and Keras using CUDA 9 and cuDNN 7 with GPU enabled, on Windows 10

First, download and install CUDA 9.0 from the [archives](https://developer.nvidia.com/cuda-toolkit-archive). Note that 9.1 is the lastest version as of 1/14/2018, but did not work with tensorflow for me.

Next, download "cuDNN v7.0.5 (Dec 5, 2017), for CUDA 9.0" from [here](https://developer.nvidia.com/rdp/cudnn-download).   Note1: Please make sure to download the version that says "for CUDA 9.0".   Note2: You will be required to make a NVIDIA Developers account for download.

Follow the instructions for cuDNN installation [here](http://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#installwindows).

Ince CUDA 9.0 and cuDNN 7 are installed, you are ready to install TensorFlow. We assume that you have anaconda installed with a current environment for use (let us call the current environment "aind"). We will first create a clone of the environment (call it "deeplearning") and activate it. Note3: Windows powershell does not work with the activate command. You must open a regular command prompt

```sh
> conda create --name deeplearning --clone aind
> activate deeplearning
```

Once the environment is active, we must install Tensorflow. However, the tensorflow-gpu build only supports CUDA 8.0. The current nightly build however does support CUDA 9.0. Install it as follows:
```sh
> pip install tf-nightly-gpu
```

Once this is installed, check if TensorFlow is properly working.
```sh
> python
>> import tensorflow
```
If everything appears to work. You can go ahead and install Keras.
```sh
> pip install keras
> python
>> import keras
```
It should now say "Using TensorFlow backend".
