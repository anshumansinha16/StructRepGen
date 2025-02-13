# Structure Representation Generation

<div align="center">

**Atomic Structure Generation from Reconstructing Structural Fingerprints**

[[arXiv](https://arxiv.org/abs/2207.13227)]

</div>

## Requirements

Git clone this repo and in the main directory do

```python
pip install -r requirements.txt
pip install -e .
```

The package has been tested on

- Python 3.6.10 / 3.9.12
- PyTorch 1.10.2 / 1.12.0
- Torch.cuda 11.3

## How to Use

Most configurations of the system/code are done through `.yaml` files under `configs/`. 

To load a configuration:

```python
# load our config yaml file
stream = open('./configs/example/example_extract_reconstruct.yaml')
CONFIG = yaml.safe_load(stream)
stream.close()
# dotdict for dot operations on Python dict 
# e.g., CONFIG.cutoff == CONFIG['cutoff']
CONFIG = dotdict(CONFIG)
```

### Representation Extraction

Extract representations for training generative model using selected descriptor.

See [`examples/example_extract.py`](https://github.com/Fung-Lab/StructRepGen/blob/main/examples/example_extract.py)

### Generative Model

Train a CVAE (conditional variational auto-encoder) as the generative model. 

See [`examples/example_cvae_trainer.py`](https://github.com/Fung-Lab/StructRepGen/blob/main/examples/example_cvae_trainer.py).

### Generation

Generate representation from a given target value using the decoder part of the CVAE. 

See [`examples/example_generator.py`](https://github.com/Fung-Lab/StructRepGen/blob/main/examples/example_generator.py).

### Reconstruction

Generate atomic structures from generated representation.

See [`examples/example_reconstruction.py`](https://github.com/Fung-Lab/StructRepGen/blob/main/examples/example_reconstruction.py).

A script to run all of the above examples is provided in `quickrun.sh`. To execute, do

```bash
chmod u+x quickrun.sh
./quickrun.sh
```
______________________________________________________________________

## Citation

```bash
@article{fung2022atomic,
  title={Atomic structure generation from reconstructing structural fingerprints},
  author={Fung, Victor and Jia, Shuyi and Zhang, Jiaxin and Bi, Sirui and Yin, Junqi and Ganesh, P},
  journal={arXiv preprint arXiv:2207.13227},
  year={2022}
}
```