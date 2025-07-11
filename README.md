# Quick‑Start Guide: Running Jupyter Notebooks on macOS Terminal
*(for Seagrass Project interns – July 2025)*

---

## 1. Prerequisites
- **macOS Terminal** (built‑in)
- **Python 3** (we’ll install it)
- **Modern web browser** (Safari, Chrome, etc.)

---

## 2. Choose Your Setup Path

### A. Homebrew + `venv` (lightweight)

```bash
# 1. Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# 2. Install Python 3
brew install python

# 3. Create project folder and enter it
mkdir ~/seagrass-notebooks && cd ~/seagrass-notebooks

# 4. Make a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# 5. Install Jupyter and dependencies
pip install notebook jupyterlab pandas opencv-python

# 6. Launch Jupyter (classic)
jupyter notebook

#    or JupyterLab
jupyter lab
```

To deactivate the environment later:

```bash
deactivate
```

### B. Conda / Miniforge (one‑stop shop)

```bash
# 1. Install Miniforge (Apple silicon build)
curl -L https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-arm64.sh -o Miniforge.sh
bash Miniforge.sh    # follow prompts, then restart Terminal

# 2. Create and activate environment
conda create -n seagrass python=3.11 jupyterlab pandas opencv -y
conda activate seagrass

# 3. Launch JupyterLab
jupyter lab
```

Install extra packages anytime:

```bash
conda install -n seagrass seaborn scikit-learn -y
```

Deactivate:

```bash
conda deactivate
```

---

## 3. First notebook test 🌊

In a new notebook cell:

```python
import cv2, pandas as pd
print("OpenCV:", cv2.__version__)
print("Pandas:", pd.__version__)
print("Notebook is talking to Python 🎉")
```

Press **Shift + Enter** – you should see the versions print.

---

## 4. Hook up the frame‑grabber script

1. Copy `extract_frames.py` (provided in our repo) into your project folder.
2. Prepare a `stamps.csv` with a column named `timestamp`.
3. Run from a notebook cell or terminal:

```bash
python extract_frames.py --video sample.mp4 --timestamps stamps.csv --out frames
```

Frames will appear in the `frames/` folder.

---

## 5. Handy cheat‑sheet 

| Task | Command |
|------|---------|
| Update pip | `python -m pip install --upgrade pip` |
| List conda envs | `conda env list` |
| Stop Jupyter | **Ctrl‑C** in Terminal, then `Y` |
| Re‑open project (venv) | `cd ~/seagrass-notebooks && source .venv/bin/activate && jupyter lab` |

---

## 6. How to share this guide

- **GitHub / GitLab**: Commit this `README.md`.
- **Notion / Confluence**: Import markdown directly.
- **Email**: Attach the `.md` file – most email clients render markdown nicely in code blocks.

---

* Reach out with any questions! Happy coding!* 
