# Continuous FairDICE Replication

This repository contains instructions to replicate **Continuous FairDICE** experiments, including environment setup, data download, training, and visualization.

---

## FairDICE Continuous Environment Installation

### Option 1: Using Docker
If Docker is available, follow the instructions in the [FairDICE repository](https://github.com/ku-dmlab/FairDICE).

### Option 2: Manual Installation (for HPC or environments without Docker)
```bash
# Clone the FairDICE repository
git clone https://github.com/ku-dmlab/FairDICE

# Manual installation MuJoCo 2.1.0
mkdir -p $HOME/.mujoco
cd $HOME/.mujoco
wget [https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz](https://mujoco.org/download/mujoco210-linux-x86_64.tar.gz)
tar -xzf mujoco210-linux-x86_64.tar.gz

# Run environment setup
./install_environment.job
```

## Installing Baselines (PEDA)
Follow instructions in the PEDA repository
```
git clone https://github.com/baitingzbt/PEDA.git
cd PEDA
conda env create -f environment.yml
conda activate peda_env
```

## Data Download
Continuous experiments use D4MORL benchmark. Download the dataset using:
```
pip install gdown
gdown --folder https://drive.google.com/drive/folders/1wfd6BwAu-hNLC9uvsI1WPEOmPpLQVT9k?usp=sharing --output data
```

## Training
For fairdice results run:
```
MO_experiments.job
```
For the baselines run:
```
PEDA_run_all.job
PEDA_preferenceweighted_all.job
```
After training the results can be visualised according to VisualizeContinuous.ipynb
