Continuous FairDICE replication
### ENVIRONMENT INSTALLATIONS
If docker is available follow the instructions in the FairDICE repo https://github.com/ku-dmlab/FairDICE

But in cases where docker is not available (like in HPC such as snellius) the following workaround is also a possibility.
git clone https://github.com/ku-dmlab/FairDICE

# Manual install of MuJoCo 2.1.0
mkdir -p $HOME/.mujoco
cd $HOME/.mujoco
wget https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz
tar -xzf mujoco210-linux-x86_64.tar.gz

Then run
./install_environment.job

In order to run the baselines follow instructions in PEDA repository https://github.com/baitingzbt/PEDA/tree/master
git clone https://github.com/baitingzbt/PEDA.git
cd PEDA
conda env create -f environment.yml
conda activate peda_env

### DATA DOWNLOAD
Continuous experiments use D4MORL benchmark. Download the dataset using:
pip install gdown
gdown --folder https://drive.google.com/drive/folders/1wfd6BwAu-hNLC9uvsI1WPEOmPpLQVT9k?usp=sharing --output data

### TRAINING
For fairdice results run:
MO_experiments.job 

For the baselines run:
PEDA_run_all.job 
PEDA_preferenceweighted_all.job

After training, the results can be visualised according to the VisualizeContin
