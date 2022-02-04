How to Finally Install TensorFlow 2 GPU on Windows 10 in 2021:

Follow this instructions here: https://towardsdatascience.com/how-to-finally-install-tensorflow-gpu-on-windows-10-63527910f255 or here: https://www.youtube.com/watch?v=hHWkvEcDBO0&t=341s

The most important step for me was the last step:

### Step 7: Install TensorFlow inside a virtual environment with Jupyter Lab

Finally, we are ready to install TensorFlow. Create a virtual environment with your preferred package manager. I use `conda`, so I create a `conda` environment named `tf` with Python version 3.8.

```
conda create -n tf python==3.8
conda activate tf
pip install --upgrade tensorflow
pip install jupyterlab ipykernel
```


It is important that both TensorFlow and JupyterLab are installed with either `pip` or `conda`. You will get a `ModelNotFoundError` in JupyterLab if they are installed from different channels.

Next, we should add the conda environment to Jupyterlab so that it is listed as a valid kernel when we launch a session:

`ipython kernel install --user --name=<name of the kernel, `tf` for our case>`

If you launch JupyterLab, you should be able to see the environment as a kernel. Create a new notebook and run this snippet to check if TF can detect your GPU:

```
import tensorflow as tf
from tensorflow.python.client import device_lib
print("Num GPUs Available: ", len(tf.config.list_physical_devices('GPU')))
device_lib.list_local_devices()
```
