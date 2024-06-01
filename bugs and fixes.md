
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

HOW TO MAKE IT WORK:
1. Copy the latent_diffusion code from the colab notebook
2. add the following lines to the code of ddpm after the line 1871:
    # LINE I ADDED
    waveform_save_path = waveform_save_path.replace("\\", "/")
    # LINE I ADDED
    waveform_save_path = waveform_save_path.replace(":", "_")
3. conda create -n audioldm_train python=3.10
4. conda activate audioldm_train
5. pip install poetry
6. poetry install
7. pip install librosa==0.9.2
8. pip install torchlibrosa == 0.0.2
9. pip install transformers == 4.30.0
10. pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118.html