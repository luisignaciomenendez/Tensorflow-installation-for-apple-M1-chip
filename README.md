# Tensorflow-installation-for-apple-M1-chip


I mainly followed the steps in : https://github.com/mrdbourke/m1-machine-learning-test with small modifications.


1. Make sure you install and activate miniforge: 

```
chmod +x ~/Downloads/Miniforge3-MacOSX-arm64.sh
sh ~/Downloads/Miniforge3-MacOSX-arm64.sh
source ~/miniforge3/bin/activate

```
2. Make a virtual environment. Some editors ( I use Atom) have the option to build this automatically. An alternative is just to follow the guide in the link and doing it with `mkdir` or also via `conda`:


```
mkdir tensorflow-test
cd tensorflow-test
conda create --prefix ./env python=3.8
conda activate ./env
```

To check that the environment was properly activated, your terminal should have moved from (base) to the name of the environment `$HOME/tensorflow-test`

Also, you can check the python version (it should be 3.8) with `python -V` . If this does not output you 3.8, make sure you go to `$HOME/tensorflow-test/bin` and look for the python versions installed there. Sometimes python 3.9 is installed (it shouldn't) and might confuse your environment. 


Then install the dependencies with conda and python pip as described in the link:



```
python -m pip install tensorflow-macos
python -m pip install tensorflow-metal
conda install jupyter pandas numpy matplotlib scikit-learn
```

Another thing I used was to make sure the kernel that I use in jupyter is actually running with python 3.8. You can create a new one (making sure you are in the cd of the virtual env in your terminal) with:

```
python -m ipykernel install --user --name mykernel --display-name "Python (tensor)"
```
When selecting a new notebook with jupyter make sure that you use this one. 

Make sure the python is the correct version again : 

```
from platform import python_version

print(python_version())

```

Now import tensroflow. To check that it is actually detecting your M1 chip with the metal plug in you can do :

```
tf.test.gpu_device_name()

```










