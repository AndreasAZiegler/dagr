1. Install the NVIDIA Container Toolkit. Follow [this guide (Installing with APt)](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html).
2. Install rocker `sudo apt install python3-rocker`
3. Build docker container
3a. `cd /path/to/dagr/docker`
3b. `docker build -t dagr .`
4. Clone DAGR repo `git clone https://github.com/AndreasAZiegler/dagr.git`
5. Build remaining dependencies:
5a. `rocker --user --nvidia --volume /path/to/dagr/:/dagr -- dagr`
5b. `conda init`
5c. `source ~/.bashrc`
5d. `conda activate dagr`
5e. `cd /dagr`
5f. `bash download_and_install_dependencies.sh`
5g. `pip install -e .`
