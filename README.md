<div align="center">
  <img src="https://github.com/tensorflow/community/blob/master/sigs/logos/SIGAddons.png" width="60%"><br><br>
</div>

-----------------

[![PyPI Status Badge](https://badge.fury.io/py/tensorflow-addons.svg)](https://pypi.org/project/tensorflow-addons/)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/tensorflow-addons)](https://pypi.org/project/tensorflow-addons/)
[![Documentation](https://img.shields.io/badge/api-reference-blue.svg)](https://www.tensorflow.org/addons/api_docs/python/tfa)
[![Gitter chat](https://img.shields.io/badge/chat-on%20gitter-46bc99.svg)](https://gitter.im/tensorflow/sig-addons)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)

## Fork made for NVIDIA Jetson Nano Jetpack 4.4 

This fork has changes made to build tensorflow-addons for Tensorflow 2.1.0+nv20.4 Jetson Nano build provided by NVIDIA.

For detailed documentation refer to original repo: https://github.com/tensorflow/addons

#### Quick Start
```
git clone https://github.com/sujeendran/tensorflow-addons.git
cd addons

pip install artifacts/tensorflow_addons-*.whl
```

#### Installing from Source
You can also install from source. This requires the [Bazel](
https://bazel.build/) build system (version >= 1.0.0).

If you have jetson_stats installed, you can use sudo jtop and enable the extra swap space as the bazel build can completely hang your system for a while(but should still build in the background very slowly even if you dont enable swap)

##### GPU and CPU Custom Ops
```
git clone https://github.com/sujeendran/tensorflow-addons.git
cd addons

export TF_NEED_CUDA="1"

# Set these if the below defaults are different on your system
export TF_CUDA_VERSION="10.2"
export TF_CUDNN_VERSION="8"
export CUDA_TOOLKIT_PATH="/usr/local/cuda"
export CUDNN_INSTALL_PATH="/usr/lib/aarch64-linux-gnu"

# This script links project with TensorFlow dependency
python3 ./configure.py

bazel build --enable_runfiles build_pip_pkg
bazel-bin/build_pip_pkg artifacts

pip install artifacts/tensorflow_addons-*.whl
```
