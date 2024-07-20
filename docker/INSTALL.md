1. Install the NVIDIA Container Toolkit. Follow [this guide (Installing with APT)](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).
2. Install rocker `sudo apt install python3-rocker`
3. Build docker container
    1. `cd /path/to/dagr/docker`
    2. `docker build -t dagr .`
4. Clone DAGR repo `git clone https://github.com/AndreasAZiegler/dagr.git`
5. Build remaining dependencies:
    1. `docker run -it --rm --runtime=nvidia --gpus all --volume /path/to/dagr:/dagr dagr`
    2. `conda init`
    3. `source ~/.bashrc`
    4. `conda activate dagr`
    5. `cd /dagr`
    6. `bash download_and_install_dependencies.sh`
    7. `pip install -e .`
6. In a different terminal run `docker ps`
7. In the same new terminal run `docker commit <CONTAINER ID> dagr`
8. Download data fragment, and checkpoint with `bash download_example_data.sh`



For lookup, not for usage:\
(5a. `rocker --user --nvidia --volume /path/to/dagr/:/dagr -- dagr`)
(5f. `bash install_env.sh`)
