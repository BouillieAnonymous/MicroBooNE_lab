## 3rd year undergraduate lab focusing on MicroBooNE experiment
### Developed by O.G. Finnerud, A. Kedziora, & J. Waiton

This folder contains almost everything that is needed to run the lab, including:

#### /data/
Data no longer included here, available at the link below.
6 files included:
- DataSet_LSND.csv: Dataset for LSND used as comparison (42.9KB).
- DataSet_MiniBooNE.csv: Dataset for MiniBoone used as comparison (17.0KB).
- data_flattened.pkl: True data from MicroBooNE flattened (24.2MB). (A)
- MC_EXT_flattened.pkl: MC and EXT data from simulations & MicroBooNE (111.4MB). (A)
- bnb_run3_mc_larcv_slimmed.h5: Event display file (77.3MB).
- oscillated_data.pkl: Data file for usage in the closure test. (140MB)

#### NOTE! All files now accessible via this link for University of Manchester students.
https://livemanchesterac-my.sharepoint.com/:u:/g/personal/john_waiton_postgrad_manchester_ac_uk/ERr7l9mqqGZIveVcVG3UD2wBrCHCYTcJPT7jIpyBOM4zZg?e=Bh2uvB



#### MainAnalysis_template.ipynb
Template for student's usage throughout the lab.

#### MicroBooNE_Y3_Labbook.pdf
PDF including all information needed to complete this lab.


#### Neutrino_functions.py
Useful functions that are used throughout the lab.


#### event_display.ipynb & EventDisplay.py
Allows for visualisation of events.

#### keras_example.ipynb and keras_example_gpu.ipynb
The original neural-network example and a TensorFlow 2 eager-mode copy for GPU backends.

### REFERENCE ENVIRONMENT (WINDOWS CPU)

Use Python 3.10.12, matching the kernel metadata in the main analysis and event display notebooks. The original `keras_example.ipynb` records Python 3.9.13; its TensorFlow 1-style session code is kept compatible by the pinned TensorFlow 2.10.1 environment. Package versions are fixed in `requirements.txt`.

Create and activate the environment, then install the pinned packages:

```powershell
conda env create -f environment.yml
conda activate microboone
python -m pip install -r requirements.txt
python -m ipykernel install --user --name microboone --display-name "Python (MicroBooNE)"
jupyter lab
```

This reference environment runs TensorFlow on the CPU in native Windows.

### NVIDIA RTX GPU ON WINDOWS (WSL2)

The detected laptop GPU is an NVIDIA GeForce RTX 5060 Laptop GPU (Blackwell, compute capability 12.0). TensorFlow's native-Windows GPU build is too old for this GPU. Use WSL2 with Docker Desktop and its NVIDIA GPU support. The Docker image is pinned to NVIDIA TensorFlow 25.02, which includes TensorFlow 2.17.0, CUDA 12.8, and a JupyterLab server optimized for Blackwell GPUs. The installed NVIDIA driver must be 570 or newer; this computer currently reports 610.88.

From PowerShell in this project folder, build and start the GPU notebook server:

```powershell
docker build -f Dockerfile.wsl-gpu -t microboone-tf-gpu .
docker run --gpus all --rm -it -p 8888:8888 -v ${PWD}:/workspace microboone-tf-gpu
```

Open the localhost URL printed by Jupyter and use `keras_example_gpu.ipynb`.

### APPLE SILICON GPU

On an Apple Silicon Mac with macOS 12 or later, install the Xcode command-line tools, create the platform environment, and install the pinned Metal build:

```bash
xcode-select --install
conda env create -f environment-macos-arm64.yml
conda activate microboone-macos-arm64
python -m pip install -r requirements-macos-arm64.txt
python -m ipykernel install --user --name microboone-macos-arm64 --display-name "Python (MicroBooNE Apple Silicon)"
jupyter lab
```

Use `keras_example_gpu.ipynb` for Metal acceleration. The original example uses TensorFlow 1-style sessions, which Apple’s Metal plugin does not support.

### INSTALLATION AND USAGE ON YEAR 3 LAB MACHINES

##### Ensure you have approximately 10GB of space on your OneDrive for this method

- Download this repository either via git or by pressing the green "Code" button and then "Download ZIP".
- Download the data required from the above mentioned 'livemanchesterac' link. 
- Extract the *uboone_lab_student_copy* folder into your local OneDrive folder.
- Extract the six files inside *data.zip/true_data/* directly into *uboone_lab_student_copy/data/* (without keeping the *true_data* subfolder).
- Begin reading through the rest of the lab script, good luck!
