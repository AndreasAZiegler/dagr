1. Install the NVIDIA Container Toolkit. Follow [this guide (Installing with APt)](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).
2. Install rocker `sudo apt install python3-rocker`
3. Build docker container
3a. `cd /path/to/dagr/docker`
3b. `docker build -t dagr .`
4. Clone DAGR repo `git clone https://github.com/AndreasAZiegler/dagr.git`
5. Build remaining dependencies:
5a. `docker run -it --rm --runtime=nvidia --gpus all --volume /path/to/dagr:/dagr dagr`
5b. `conda init`
5c. `source ~/.bashrc`
5d. `conda activate dagr`
5e. `cd /dagr`
5f. `bash install_env.sh`
5f. `bash download_and_install_dependencies.sh`
5g. `pip install -e .`
6. In a different terminal run `docker ps`
7. In the same new terminal run `docker commit <CONTAINER ID> dagr`
6. Download data fragement, and checkpoint with `bash download_example_data.sh`



For lookup, not for usage:
(5a. `rocker --user --nvidia --volume /path/to/dagr/:/dagr -- dagr`)
