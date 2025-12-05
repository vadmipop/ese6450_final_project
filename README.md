# ESE 6450 Final Project (John Harshith, Aniket Ghorpade, Vadim Popov)

## Blended Latent Diffusion

### Environment setup

Vadim ran BLD code on `runpod.io` – a cloud computing platform that provides on-demand GPUs. That's why BLD env setup is slightly different from the other two baselines. Here are the steps:

1) Create a pod on `runpod.io` – select Network Volume option to ensure higher GPU availability.
2) Install `conda` and create a new environment via `conda create -n p2p python=3.9 -y`.
3) Run `pip install -r p2p_requirements.txt`.
4) Clone `PnPInversion` repo into `/workspace`.
5) Copy `.bashrc` and `.condarc` files into `/workspace`.
6) Run the following set of commands on every startup:
```
apt update && apt install sudo
sudo apt-get update -y
sudo apt-get install tmux -y
sudo apt-get install nano -y
rm -f ~/.bashrc
ln -s /workspace/bashrc_persistent ~/.bashrc
rm -f ~/.condarc
ln -s /workspace/.condarc ~/.condarc

source ~/.bashrc

conda activate p2p
cd /workspace/PnPInversion/
```
### Running the code
1) Run `python run_bld_adaptive_mask.py`
2) For evaluation, run 
`python evaluation/evaluate.py --result_path evaluation/results/bld_adaptive_mask.csv --tgt_methods 2_bld_adaptive_mask` (you might need to configure a few variables in the evaluation script to take in modified adaptive mask names).

**NOTE:** For reproducability purposes, Vadim used RTX 4090 for running both the baseline and the improved version.



