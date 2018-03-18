# Install instructions for TensorFlow and Keras using CUDA 9 and cuDNN 7 with GPU enabled, on Windows 10

Latest update date: 03/18/2018

**Step 1:** First, let's make sure the system satisfies the hardware requirements, and let's pick the right version of tensorflow based on your hardware:

1. Make sure a compatible GPU is installed. Not all CUDA capable GPUs are supported by tensorflow. TensorFlow requires a compute compatibility of 3.0 or higher. A list of nVidia GPUs with compute compatibility can be found [here](https://developer.nvidia.com/cuda-gpus/).
2. Check if your CPU is AVX compatible (a list of CPUs can be found [here](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions)). If your CPU does not support AVX, you will need to install tensorflow 1.5 instead of tensorflow 1.6. Use tensorflow-gpu==1.5 in the tensorflow installation line in Step 4 below and that should be it.


**Step 2:** Next, download and install CUDA 9.0 from the [archives](https://developer.nvidia.com/cuda-toolkit-archive). Note that 9.1 or later versions are NOT compatible with the current versions of tensorflow. I will update this as and when they become compatible.

Also download "cuDNN v7.0.5 (Dec 5, 2017), for CUDA 9.0" from [here](https://developer.nvidia.com/rdp/cudnn-download).   Note1: Please make sure to download the version that says "for CUDA 9.0".   Note2: You will be required to make a NVIDIA Developers account for download.  Note3: Please download v7.0.5 and NOT v7.1 of cuDNN as current tensorflow versions are compiled with cuDNN v7.0.5.

Follow the instructions for cuDNN installation [here](http://docs.nvidia.com/deeplearning/sdk/cudnn-install/index.html#installwindows).

Once CUDA 9.0 and cuDNN 7 are installed, you are ready to install TensorFlow. If you use conda, I suggest cloning the environment. You can skip Step 3 if you do not use conda.

**Step 3:**  We assume that you have anaconda installed with a current environment for use (let us call the current environment "aind"). We will first create a clone of the environment (call it "deeplearning") and activate it. Note3: Windows powershell does not work with the activate command. You must open a regular command prompt

```sh
> conda create --name deeplearning --clone aind
> activate deeplearning
```

Once the environment is active, we must install Tensorflow. 

**Step 4:** Install tensorflow-gpu as follows:
```sh
> pip install tensorflow-gpu==1.6
```

Once this is installed, check if TensorFlow is properly working.
```sh
> python
>> import tensorflow
```

You can check the list of devices using the following:

```sh
>> from tensorflow.python.client import device_lib
>> device_lib.list_local_devices()
```

This should show your your CPU and GPUs listed. If it does not show the GPU, please see the troubleshooting section below. If everything appears to work. You can go ahead and install Keras.
```sh
> pip install keras
> python
>> import keras
```
It should now say "Using TensorFlow backend".

## Troubleshooting
1. Please make sure that the right versions of CUDA and cuDNN are installed
2. You will need to install tensorflow-gpu 1.5 or 1.6 to enable CUDA 9.0 and cuDNN 7 support. Prior versions don't support this.
3. Ensure that environment variables are correctly set. The system variables must have the following in them:

    | Variable | Must contain Value|
    | --- | --- |
    |CUDA_PATH| C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0 |
    |CUDA_PATH_V9_0 | C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0|
    | Path | C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\bin |
    |Path | C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0\libnvvp|
4. Make sure a compatible GPU is installed. Not all CUDA capable GPUs are supported by tensorflow. TensorFlow requires a compute compatibility of 3.0 or higher. A list of nVidia GPUs with compute compatibility can be found [here](https://developer.nvidia.com/cuda-gpus/).
5. If you are using tensorflow-gpu 1.6, make sure your CPU supports AVX (a list of CPUs can be found [here](https://en.wikipedia.org/wiki/Advanced_Vector_Extensions)). If your CPU does not support AVX, use tensorflow-gpu==1.5 in the tensorflow installation line above and it should solve the issue.
