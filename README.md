# Record linkage on synthetic demographic data using ML

This repository contains notebooks and code for training and running inference using demographic data.

## Notebooks

## Prerequisites

- Python 3.11 is preferred (some Snowflake packages have newer dependency requirements).

## Setup

1. Ensure the `requirements.in` file is present in the repository.

2. This project used `uv` to compile the requirements file. Install `uv` and regenerate `requirements.txt` from `requirements.in` if you need to update or re-pin dependencies:

```bash
pip install uv
uv pip compile requirements.in -o requirements.txt
```

3. Create and activate a virtual environment, ensure `pip` is present/upgraded in the venv, then install dependencies:

Make sure the Python launcher `py` is installed and recognized by your system. Verify the launcher and target Python version:

```powershell
py -3.11 --version
```

If `py -3.11` is available, create the venv explicitly with Python 3.11 (recommended):

Windows (PowerShell):

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
# Ensure pip is available and upgraded inside the venv
py -3.11 -m ensurepip --upgrade
py -3.11 -m pip install --upgrade pip
pip install -r requirements.txt
```

Windows (cmd):

```cmd
py -3.11 -m venv .venv
.\.venv\Scripts\activate
py -3.11 -m ensurepip --upgrade
py -3.11 -m pip install --upgrade pip
pip install -r requirements.txt
```

If the `py` launcher is not available, ensure that the `python` command on PATH points to Python 3.11 and use `python -m venv .venv` instead.

## Notes

**Prevent committing notebook outputs (PHI):**

- **Why:** Notebook outputs can contain protected health information (PHI). Even though synthetic data is used in this project, it is reccommended to use `nbstripout` to automatically strip outputs before commits so PHI is not accidentally committed to git.
- **Install & enable locally:**

```bash
pip install nbstripout
nbstripout --install
# To also install repository attributes (.gitattributes) so other clones respect stripping:
nbstripout --install --attributes .gitattributes
```

- **Undo:**

```bash
nbstripout --uninstall
```

These steps ensure cell outputs are removed from notebooks at commit-time. Consider adding a pre-commit CI check if you want repository-level enforcement.
