
BUG: ModuleNotFoundError: No module named 'audioldm_train'     
FIX: Set the working directory to "AudioLDM-training-finetuning"

BUG: ModuleNotFoundError: No module named 'taming'
FIX: pip install taming-transformers-hugf
and change the line in "contperceptual.py":
""""
from taming_transformers_hugf.taming.modules.losses.vqperceptual import *  # TODO: taming dependency yes/no?
""""

BUG: RuntimeError: Distributed package doesn't have NCCL built in
FIX: maybe remove the strategy=DDPStrategy from the Trainer

BUG: wandb.errors.UsageError: api_key not configured (no-tty). call wandb.login(key=[your_api_key])
FIX: 