## Installation

### Installing Requirements on Colab

Create a requirements file:

```python
%%writefile requirements.txt

gymnasium[atari]==0.29.1
gymnasium[classic-control]==0.29.1
gymnasium[accept-rom-license]==0.29.1
moviepy==1.0.3
numpy<2
opencv-python==4.10.0.84
torch==2.5.0
torchvision==0.20.0
pytorch-ignite==0.5.1
tensorboard==2.18.0
mypy==1.8.0
ptan==0.8.1
stable-baselines3==2.3.2
torchrl==0.6.0
ray[tune]==2.37.0
pytest
```

Install the requirements:

```python
!pip install -r requirements.txt
```

## Setup

### Upload to Google Drive

Upload this repository folder to your drive first.

### Mounting Google Drive

```python
from google.colab import drive
drive.mount('/content/drive', force_remount=True)
```

### Update Import Statements

Change your import statements to use the files from Google Drive:

```python
# From:
# from lib import dqn_model, common

# To:
from drive.MyDrive.DRL.Chapter08.lib import dqn_model, common
```

### Create TensorBoard Directory in Drive

```python
!mkdir drive/MyDrive/DRL/Chapter08/run
!mkdir drive/MyDrive/DRL/Chapter08/run/log
```

### Update Log Directory Paths

Change the log directory path in all relevant files (example from Chapter 8's `lib/common.py`):

```python
# From:
# logdir = f"runs/{now}-{params.run_name}-{run_name}"

# To:
logdir = f"drive/MyDrive/DRL/Chapter08/run/log/{now}-{params.run_name}-{run_name}"
```

## Running TensorBoard

Load the TensorBoard extension in Colab:

```python
%load_ext tensorboard
```

Start TensorBoard with the correct log directory:

```python
%tensorboard --logdir "drive/MyDrive/DRL/Chapter08/run/log"
```
