# LiDAR-Bonnetal Training

This part of the framework deals with the training of segmentation networks for point cloud data using range images.

## Tasks

- [Semantic Segmentation](tasks/semantic).
- [Panoptic Segmentation](tasks/panoptic) \[Soon\].

## Dependencies

First you need to install the nvidia driver and CUDA, so have fun!

- CUDA Installation guide: [link](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)

- System dependencies:

  ```sh
  $ sudo apt-get update 
  $ sudo apt-get install -yqq  build-essential ninja-build \
    python3-dev python3-pip apt-utils curl git cmake unzip autoconf autogen \
    libtool mlocate zlib1g-dev python3-numpy python3-wheel wget \
    software-properties-common openjdk-8-jdk libpng-dev  \
    libxft-dev ffmpeg python3-pyqt5.qtopengl
  $ sudo updatedb
  ```

- Python dependencies
  - first apt install python3-tk python3-distutils
  -
    ```sh
    $ sudo pip3 install -r requirements.txt
    ```
  - install `torch` and `torchvision`. In order case they must be special versions, so must be installed manually (see requirements.txt file)

## Running
- active the venv in which requirements were installed
- `cd train/tasks/semantic/`
- For inference:

  `python infer.py -d __pointcloud_folder__ -m __model_folder__ -ac __arch_cfg_yaml__`

  - `__pointcloud_folder__` must be a path to a folder containing pointclouds recorded as .bin or .pcd. its structure must be `__pointcloud_folder__/sequences/xx/velodyne/...` where 'xx' are numbers of sequences to be used (and corresponds to the those configured in data_cfg)
  - `__model_folder__`should contain the model and config files
  - `__arch_cfg_yaml__` should be the name of the arch config file to be used, iof not using the default 'arch_cfg.yaml'
  - see `python infer.py -h` for more args

  In the end of the of the inference, the script will print the path to the log folder where the inference results were saved

- Visualize inference results:

  `python visualize.py -d __pointcloud_folder__ -s 00 -ac __arch_cfg_yaml__ -p __log_folder__`

  - `__pointcloud_folder__` and ``__arch_cfg_yaml__` same as for inference
  - `__log_folder__` is the folder with the inference results


