# AlphaZero for Exact Unitary Synthesis

This repo contains the code used to produce the results of [Unitary Synthesis with AlphaZero via Dynamic Circuits](https://scirate.com/arxiv/2508.21217).
It contains two submodules:  
    - a fork of `turbozero` : a full JAX implementation of AlphaZero agents, modified to better fit this project.  
    - `quantum_compilation` : a full JAX implemenation of quantum circuit simulation, with support of clean ancillae.

## Installation

First clone the repo and its submodules

```
git clone --recurse-submodules https://github.com/xvalcarce/az_eus
```

Setup using a [miniconda](https://www.anaconda.com/docs/getting-started/miniconda/main) environment

```
conda env create --file environment.yml
conda activate az_eus
python -m pip install -e turbozero
python -m pip install -e quantum_compilation
```

In order to use jupyter notebooks (and kernel) inside the `az_eus` conda environment, run

```
conda install jupyterlab
pip install ipykernel
python -m ipykernel install --user --name az_eus --display-name "Python (az_eus)"
```

You can now start jupyter using the `jupyter lab` command, select the `Python (az_eus)` kernel.

## Training an agent

Start jupyter lab using `jupyter lab` within the conda env `az_eus`. Open the `train_agent.ipynb` notebook.
Edit `quantum_compilation/config.ini` to chose your environment parameters, e.g. number of qubits, ancillae, gateset, connectivity.
Edit `notebook/train.ini` to set agent and training loop parameters, e.g. AlphaZero hyperparameters.
Run the notebook. Data will be saved in the `data` directory.

## Synthesis using a trained agent

We provide 3 trained agents, please download them [here](https://sharebox.ipht.fr/index.php/s/fIox0qxZKcADM0d) and extract the archive in the `data/` directory.

Start jupyter lab using `jupyter lab` within the conda env `az_eus`. Open the `synthesis.ipynb` notebook.
Select the agent type in the second cell of the notebook. Run the `compile` function on the target unitary of your choice.
