# Python Virtual Environment, Jupyter Kernel & Running Code

This guide shows how to:

1. Create a **virtual environment**  
2. Install packages  
3. Create a **Jupyter kernel** from that environment  
4. Run **Python scripts** and **notebooks**

Examples are for **Windows (PowerShell/CMD)**.

---

## 1. Create a Virtual Environment

From your project folder (replace the path with your own):

```powershell
cd C:\path\to\your\project

# Create a venv called ".venv" using Python 3
py -3 -m venv .venv
or create venv with **Python 3.13**
py -3.13 -m venv .venv
# (optional) verify Python version
.\.venv\Scripts\python.exe -c "import sys; print(sys.version)"

```

### Activate the environment

**PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

**CMD:**

```cmd
.\.venv\Scripts\activate.bat
```

You should see `(.venv)` in front of your prompt.

To **deactivate** later:

```powershell
deactivate
```

---

## 2. Install Packages

Inside the activated venv:

```powershell
# Optional: upgrade pip
python -m pip install --upgrade pip

# If you have a requirements file
python -m pip install -r requirements.txt

# Or install packages one by one
python -m pip install numpy pandas matplotlib jupyter

# Install dependencies in venv from src\requirements.txt  
cd C:\Users\xxx\Documents\workspace\xxx
.\.venv\Scripts\python.exe -m pip install --upgrade pip
.\.venv\Scripts\python.exe -m pip install -r src\requirements.txt

```

---

## 3. Create a Jupyter Kernel from the venv

This lets you select this environment inside Jupyter notebooks.

Still inside the activated venv:

```powershell
python -m pip install ipykernel

# Create a named kernel
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"
```

Now, when you open a notebook, you can choose **“Python (myenv)”** as the kernel.

If you ever want to remove that kernel:

```powershell
jupyter kernelspec uninstall myenv
```

---

## 4. Run a Python Script

From your project directory, with the venv activated:

```powershell
python script_name.py
```

Examples:

```powershell
python train.py
python main.py
python tools\convert_data.py
```

If the script asks for input (via `input()`), type your answer and press Enter.

---

## 5. Work with Jupyter Notebooks

### 5.1 Start Jupyter

With the venv activated:

```powershell
jupyter notebook
# or
jupyter lab
```

A browser window will open. Create or open a `.ipynb` file, then select the kernel:

- **Kernel → Change Kernel → “Python (myenv)”**

### 5.2 Run All Cells

In the notebook UI:

- Use **Run → Run All Cells** (or the “Run All” button)
- Or run cells one by one with Shift+Enter

---

## 6. Run a Notebook from the Command Line (Optional)

You can execute a notebook non‑interactively and save the output:

```powershell
# Ensure nbconvert is installed
python -m pip install nbconvert

# Run notebook in-place
python -m jupyter nbconvert --to notebook --execute "notebook.ipynb" --inplace
```

This will run all cells and write results into the same `.ipynb` file.

---

## 7. Quick Summary of Commands

```powershell
# Create venv
py -3 -m venv .venv

# Activate (PowerShell)
.\.venv\Scripts\Activate.ps1

# Install deps
python -m pip install -r requirements.txt

# Make Jupyter kernel
python -m pip install ipykernel jupyter
python -m ipykernel install --user --name myenv --display-name "Python (myenv)"

# Run a script
python script_name.py

# Start Jupyter
jupyter notebook
# or
jupyter lab
```

## Examples 
```
PS C:\Users\xxx\Documents\workspace\Submission_Everything> .venv\Scripts\python.exe -m ipykernel install --user --name eeg_artifact_py313 --display-name "Python 3.13 (eeg_artifact)"

PS C:\Users\xxx\Documents\workspace\Submission_Everything> .venv\Scripts\python.exe .\src\test.py
C:\Users\xxx\Documents\workspace\Submission_Everything
```


