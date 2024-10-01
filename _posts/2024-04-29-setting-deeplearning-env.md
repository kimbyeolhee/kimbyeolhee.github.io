---
layout: post
title: Setting up deep learning environment
date: 2024-09-29 13:39:00
description:
tags: conda gpu
categories: env
citation: true
images:
  slider: true
citation: false
---

## 1. Install Anaconda

<br>

Download and install the appropriate version for your system from [here](https://www.anaconda.com/download)

<br>

<div style="width: 60%; margin: 0 auto;">
  <swiper-container keyboard="true" navigation="true" pagination="true" pagination-clickable="true" pagination-dynamic-bullets="true" rewind="true">
    <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_1.png" class="img-fluid rounded z-depth-1" zoomable=true %}</swiper-slide>
    <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_2.png" class="img-fluid rounded z-depth-1" zoomable=true %}</swiper-slide>
    <swiper-slide>{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_3.png" class="img-fluid rounded z-depth-1" zoomable=true %}</swiper-slide>
  </swiper-container>
</div>

<br>

Once you install anaconda successfully, you can run the Anaconda prompt.


<br>

## 2. Creating Virtual Environment

<br>

* Create a new environment with the desired Python version.

```sh
(base) C:\Users\User> conda create -n <custom_name> python=3.10
```

<br>

* Activate the environment. then you can see the front of the bracket name is changed.

```sh
(base) C:\Users\User> conda activate <custom_name>

(<custom_name>) C:\Users\User>
```

<br>

* Install additional packages.

First, I'm gonna install pytorch **CPU** version. <br>
Select your preferences and run the install command on [here](https://pytorch.org/get-started/locally/)

<div style="width: 70%; margin: 0 auto;">
{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_4.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

<br>

If you want to check the installed packages, you can use the following command.

```sh
(<custom_name>) C:\Users\User>pip show torch
Name: torch
Version: 2.3.0
Summary: Tensors and Dynamic neural networks in Python with strong GPU acceleration
Home-page: https://pytorch.org/
Author: PyTorch Team
Author-email: packages@pytorch.org
License: BSD-3
Location: c:\users\user\miniconda3\envs\py310\lib\site-packages
Requires: filelock, fsspec, jinja2, mkl, networkx, sympy, typing-extensions
Required-by: torchvision
```

<br>

## 3. Setting anaconda env on VScode terminal (Optional/Windows)

<br>

* Open VScode and press `Ctrl + Shift + P` to open the command palette.
* Type `Setting JSON` and select `Preferences: Open User Settings (JSON)` from the list.
* Add the anaconda path to the settings.json file.
* below the code, paste your own path on `"args": ["/K", "{paste your own path here}"]`
  * you can find your own path by right clicking on Anaconda Prompt and selecting `Properties`

<br>

  <div style="width: 40%; margin: 0 auto;">
  {% include figure.liquid loading="eager" path="assets/img/blog/241001_env_5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>

<br>

```json
"terminal.integrated.profiles.windows": {
    "Conda": {
        "path": [
            "C:\\Windows\\System32\\cmd.exe"
        ],
        "args": [
            "/K",
            "{🖋️paste your own path here}"
        ]
    }
},
"terminal.integrated.defaultProfile.windows": "Conda"
```

<br>

## 4. Install Pytorch GPU version

<br>

If you have a GPU, you can install the GPU version of PyTorch.

* **Download NVIDIA GPU Driver**
  * Download the appropriate version for your system from [here](https://www.nvidia.com/ko-kr/drivers/) and install it.

<div style="width: 40%; margin: 0 auto;">
{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_6.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

<br>

  * If you install it successfully, you can check `nvidia-smi` on your terminal.

<br>

```sh
(py310) C:\Users\User>nvidia-smi
Tue Oct  1 21:38:25 2024
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 561.09                 Driver Version: 561.09         CUDA Version: 12.6     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                  Driver-Model | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3060      WDDM  |   00000000:01:00.0  On |                  N/A |
|  0%   49C    P8             12W /  170W |    1190MiB /  12288MiB |     15%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A      2536    C+G   ...5n1h2txyewy\ShellExperienceHost.exe      N/A      |
|    0   N/A  N/A      2796    C+G   ...oogle\Chrome\Application\chrome.exe      N/A      |
|    0   N/A  N/A      7192    C+G   ...r\AppData\Roaming\Zoom\bin\Zoom.exe      N/A      |
|    0   N/A  N/A      7688    C+G   ...CBS_cw5n1h2txyewy\TextInputHost.exe      N/A      |
|    0   N/A  N/A      9212    C+G   C:\Windows\explorer.exe                     N/A      |
|    0   N/A  N/A     10600    C+G   ...nt.CBS_cw5n1h2txyewy\SearchHost.exe      N/A      |
|    0   N/A  N/A     10624    C+G   ...2txyewy\StartMenuExperienceHost.exe      N/A      |
|    0   N/A  N/A     14064    C+G   ...__8wekyb3d8bbwe\WindowsTerminal.exe      N/A      |
|    0   N/A  N/A     15212    C+G   ...crosoft\Edge\Application\msedge.exe      N/A      |
|    0   N/A  N/A     16680    C+G   ...e Stream\97.0.1.0\GoogleDriveFS.exe      N/A      |
|    0   N/A  N/A     17988    C+G   ...\Docker\frontend\Docker Desktop.exe      N/A      |
|    0   N/A  N/A     19716    C+G   ...on\129.0.2792.65\msedgewebview2.exe      N/A      |
|    0   N/A  N/A     20084    C+G   ...ta\Local\Programs\cursor\Cursor.exe      N/A      |
|    0   N/A  N/A     21452    C+G   ...0.0_x64__p7pnf6hceqser\snipaste.exe      N/A      |
|    0   N/A  N/A     21796    C+G   ...on\129.0.2792.65\msedgewebview2.exe      N/A      |
|    0   N/A  N/A     21808    C+G   ...Programs\Microsoft VS Code\Code.exe      N/A      |
|    0   N/A  N/A     24448    C+G   ...on\129.0.2792.65\msedgewebview2.exe      N/A      |
+-----------------------------------------------------------------------------------------+
```

<br>

* **Install CUDA**
  * Check the compute capability of your GPU from [here](https://developer.nvidia.com/cuda-gpus).
    * In my case, My GPU is NVIDIA GeForce RTX 3060. So compute capability is **8.6**.

  * My compute capability is 8.6, so it's working on **11.1 ~ 12.2** version.

<div style="width: 60%; margin: 0 auto;">
{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_7.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

  <br>

  * Now, download the pytorch GPU version with CUDA from [here](https://pytorch.org/get-started/locally/)
    * I will choose `Conda` instead of `pip`. Because when you install **Pytorch GPU**, you have to install **CUDA toolkit** and **CUDNN** too. But if you choose `Conda`, you don't have to install them separately. Conda will install them automatically.
    * I choose `CUDA 12.2` because my compute capability is working on **11.1 ~ 12.2** version.

<div style="width: 60%; margin: 0 auto;">
{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_8.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

<br>

  * If pytorch GPU is installed successfully, you can check it by the following command `torch.cuda.is_available()`.

```sh
(<custom_name>) C:\Users\User>python
Python 3.10.14 | packaged by Anaconda, Inc. | (main, May  6 2024, 19:44:50) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import torch
>>> torch.cuda.is_available()
True
```

<br>

## 5. Install Jupyter Notebook (Optional)

<br>

With Jupyter Notebook, it's easy to debug the code by function unit.


* Install Jupyter Notebook

```sh
(<custom_name>) C:\Users\User>pip install jupyter
```

<br>

* Run Jupyter Notebook on your own IDE(I'm using VScode).
  * On VScode, install `Jupyter` extension first.

  * make `.ipynb` file.

  * Select the kernel as your environment that you made before.

<br>

<div style="width: 60%; margin: 0 auto;">
{% include figure.liquid loading="eager" path="assets/img/blog/241001_env_9.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

<br>