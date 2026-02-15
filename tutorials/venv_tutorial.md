# Python Virtual Environments Tutorial

A practical guide to using Python virtual environments (`venv`) for this project.

## Why Virtual Environments?

When you install Python packages with `pip`, they go into a global location by default. This causes problems:

- **Project A** needs `pandas 1.5` but **Project B** needs `pandas 2.0`
- Installing a package for one project might break another
- You can't tell which packages a specific project actually uses
- Deploying your project on another machine becomes guesswork

A virtual environment solves this by giving each project its own isolated set of packages. Packages installed in one environment don't affect any other.

## How It Works

A virtual environment is a directory (usually called `venv`) that contains:

- A copy of (or symlink to) the Python interpreter
- Its own `pip` installer
- An isolated `site-packages/` directory for installed packages

When you "activate" an environment, your shell is configured to use that directory's Python and pip instead of the system-wide ones.

```
System Python (/usr/bin/python3)
├── numpy 1.24
├── pandas 1.5
└── hundreds of other packages...

Project venv (./venv/bin/python)
├── pandas 2.1        ← only what this project needs
├── scikit-learn 1.3
└── jupyter 1.0
```

## Creating a Virtual Environment

### Prerequisites

Make sure Python 3 is installed:

```bash
python3 --version
```

The `venv` module is included with Python 3.3+. On some Linux distributions, you may need to install it separately:

```bash
# Debian/Ubuntu
sudo apt install python3-venv
```

### Create the Environment

Navigate to the project directory and create the environment:

```bash
cd W26-MDST-Project_Heart-Failure-Survival-Analysis
python3 -m venv venv
```

This creates a `venv/` directory inside the project. The name `venv` is a convention; you could name it anything, but `venv` is widely recognized.

## Activating and Deactivating

### Activate

You must activate the environment each time you open a new terminal.

**Linux / macOS:**

```bash
source venv/bin/activate
```

**Windows (Command Prompt):**

```cmd
venv\Scripts\activate.bat
```

**Windows (PowerShell):**

```powershell
venv\Scripts\Activate.ps1
```

When activated, your terminal prompt changes to show the environment name:

```
(venv) user@machine:~/project$
```

### Verify Activation

```bash
# Should point to the venv directory, not the system Python
which python

# Example output:
# /home/you/W26-MDST-Project_Heart-Failure-Survival-Analysis/venv/bin/python
```

### Deactivate

When you're done working on the project:

```bash
deactivate
```

Your prompt returns to normal, and `python`/`pip` point to the system installation again.

## Installing Packages

With the environment activated, install packages using `pip`:

```bash
# Install a single package
pip install pandas

# Install a specific version
pip install pandas==2.1.0

# Install all project dependencies from requirements.txt
pip install -r requirements.txt
```

For this project, the required packages are:

```
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
statsmodels
jupyter
```

All of these are installed with:

```bash
pip install -r requirements.txt
```

### Checking Installed Packages

```bash
# List all installed packages
pip list

# Show details about a specific package
pip show pandas
```

## The `requirements.txt` File

This file lists all the packages your project needs. It allows anyone to recreate the same environment.

### Generating `requirements.txt`

```bash
# Export currently installed packages with exact versions
pip freeze > requirements.txt
```

This produces output like:

```
numpy==1.26.2
pandas==2.1.4
scikit-learn==1.3.2
...
```

### Simplified vs. Pinned Requirements

This project uses **simplified** requirements (no version numbers):

```
pandas
numpy
matplotlib
```

This installs the latest compatible versions. For reproducibility in production, you'd pin exact versions:

```
pandas==2.1.4
numpy==1.26.2
matplotlib==3.8.2
```

Both approaches are valid. Simplified is more convenient for educational projects; pinned is safer for production.

## Complete Setup Walkthrough

Here's the full process for getting this project running from scratch:

```bash
# 1. Clone the repository
git clone https://github.com/MichiganDataScienceTeam/W26-MDST-Project_Heart-Failure-Survival-Analysis.git
cd W26-MDST-Project_Heart-Failure-Survival-Analysis

# 2. Create a virtual environment
python3 -m venv venv

# 3. Activate it
source venv/bin/activate   # Linux/macOS
# venv\Scripts\activate    # Windows

# 4. Install dependencies
pip install -r requirements.txt

# 5. Launch Jupyter
jupyter notebook

# 6. When done, deactivate
deactivate
```

## Common Issues and Fixes

### "command not found: python"

On some systems, Python 3 is only available as `python3`:

```bash
python3 -m venv venv
```

### "No module named venv"

Install the venv module (Debian/Ubuntu):

```bash
sudo apt install python3-venv
```

### "pip installs packages globally even though venv is active"

Make sure the environment is actually activated. Check with:

```bash
which pip
# Should show: .../venv/bin/pip
# NOT: /usr/bin/pip
```

If it shows the system path, re-activate:

```bash
source venv/bin/activate
```

### "I accidentally committed the `venv/` directory"

The `venv/` directory should never be committed. It's already in this project's `.gitignore`. If it was committed by mistake:

```bash
# Remove from git tracking (keeps files on disk)
git rm -r --cached venv/
git commit -m "Remove venv from version control"
```

### Jupyter Notebook doesn't see my packages

If Jupyter can't import packages you installed in the venv, the notebook may be using a different Python kernel. Fix this by installing the kernel from within the activated venv:

```bash
pip install ipykernel
python -m ipykernel install --user --name=venv --display-name="Python (venv)"
```

Then in Jupyter, go to **Kernel > Change Kernel** and select **Python (venv)**.

## Best Practices

1. **Always use a virtual environment** for Python projects. Never install project dependencies globally.

2. **Don't commit `venv/`** to version control. It's large, system-specific, and reproducible from `requirements.txt`. The `.gitignore` in this project already handles this.

3. **Keep `requirements.txt` updated.** When you add a new package, add it to the requirements file so others can install it too.

4. **Activate before working.** Every time you open a new terminal to work on the project, activate the environment first.

5. **One environment per project.** Don't share environments across projects; that defeats the purpose of isolation.

## `venv` vs. Other Tools

| Tool | When to Use |
| --- | --- |
| `venv` | Built-in, no extra install needed. Good for most projects. **Use this one.** |
| `virtualenv` | Third-party predecessor to `venv`. Faster creation, more features. Same concept. |
| `conda` | Manages Python itself + non-Python dependencies (C libraries, R, etc.). Common in data science. Heavier. |
| `poetry` | Combines dependency management + packaging. Good for libraries you publish. |
| `pipenv` | Combines `pip` + `venv` with a lockfile. Less commonly used now. |

For this project, `venv` is sufficient and recommended.

## Quick Reference

| Command | What It Does |
| --- | --- |
| `python3 -m venv venv` | Create a virtual environment |
| `source venv/bin/activate` | Activate (Linux/macOS) |
| `venv\Scripts\activate` | Activate (Windows) |
| `deactivate` | Deactivate the environment |
| `pip install <package>` | Install a package |
| `pip install -r requirements.txt` | Install all project dependencies |
| `pip list` | List installed packages |
| `pip freeze > requirements.txt` | Export installed packages |
| `which python` | Verify which Python is active |

## Further Reading

- [Python docs: venv](https://docs.python.org/3/library/venv.html)
- [Real Python: Virtual Environments Primer](https://realpython.com/python-virtual-environments-a-primer/)
- [Python Packaging User Guide](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/)
