# Machine Learning Labs

Master Smart Data, ENSAI · Machine Learning labs (2 hours each)

| Lab | Folder | Notebook | Topics |
|---|---|---|---|
| 1 | `lab1-regression` | `lab_regression.ipynb` | OLS, multiclass logistic regression, Ridge, introduction to inverse problems |
| 2 | `lab2-svm-knn` | `lab_svm_knn.ipynb` | SVM and the kernel trick, kNN for classification and regression, dimension reduction with gradients |
| 3 | `lab3-ensembles` | `lab_ensembles.ipynb` | Decision trees, boosting (AdaBoost, gradient boosting, XGBoost), bagging and random forests |

All the labs share **one** repository and **one** virtual environment. You install it once, before the first lab, by following the steps below **in order**. It takes about 10 minutes.

Before each new lab, you only need to update your copy (section *Getting a new lab*).

---

## Why a virtual environment?

A **virtual environment** (venv) is a private folder that contains its own Python packages.
Each project gets its own environment, so:

* the packages of these labs do not interfere with your other projects,
* anyone can rebuild exactly the same environment from the file `requirements.txt`.

This is standard practice for any Python project, in research as in industry.

---

## Step 1. Get the labs on your machine

Open a terminal.

Move to the folder where you keep your courses, for example:

```bash
cd Documents
```

Then download the repository with Git:

```bash
git clone https://github.com/thibault-pautrel/ml-labs.git
cd ml-labs
```

**No Git on your machine?** On the GitHub page of the repository, click the green **Code** button,
then **Download ZIP**. Unzip the folder, then move into it with `cd` in your terminal.
You will then have to download the ZIP again for each new lab.

Check that you are in the right folder: the command `dir` (Windows) or `ls` (macOS, Linux)
must list `README.md`, `requirements.txt` and the folders `lab1-regression`, `lab2-svm-knn`, and so on.

## Step 2. Create the virtual environment

From the `ml-labs` folder:

```bash
python -m venv .venv
```

This creates a folder `.venv` at the root of the repository. All the labs use it. On macOS and Linux, if `python` is not found, use `python3`.

## Step 3. Activate it

| System | Command |
|---|---|
| Windows (`cmd`) | `.venv\Scripts\activate` |
| macOS, Linux | `source .venv/bin/activate` |

Your prompt now starts with `(.venv)`. This tells you that the environment is active.
You must activate it again **each time you open a new terminal**.

## Step 4. Install the packages

With the environment active:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

This installs `numpy`, `scipy`, `matplotlib`, `scikit-learn`, `pandas`, `xgboost` and `ipykernel` (what VS Code needs to run a notebook) **inside** `.venv` only.

Do not skip the first command: an old version of `pip` can fail to install some packages.

## Step 5. Open a notebook

**Option A (recommended): VS Code.** Open the `ml-labs` folder in VS Code (*File > Open Folder*), then open the notebook of the lab, for example `lab2-svm-knn/lab_svm_knn.ipynb`.
Click on *Select Kernel* at the top right, and choose the interpreter located in `.venv`.
If VS Code asks to install the *Python* or *Jupyter* extensions, accept.

**Option B: Jupyter in the browser.** From the same terminal, with `(.venv)` active, install Jupyter, then start it from the `ml-labs` folder:

```bash
pip install notebook
jupyter notebook
```

A browser tab opens. Open the folder of the lab, then click on its notebook.

## Step 6. Check your installation

Run the first code cell of the notebook (Part 0). It must print `Environment OK`.
You are ready.

---

## Getting a new lab

A new folder appears in the repository before each lab. To get it, open a terminal in the `ml-labs` folder and run:

```bash
git pull
```

Then activate the environment (Step 3) and install the packages again, in case the new lab needs a new one:

```bash
pip install -r requirements.txt
```

**You cloned the repository under its old name, `lab-regression`?** Nothing to do: GitHub redirects the old address, and `git pull` works as usual. The folder on your machine keeps its old name, which is fine.

**`git pull` refuses: "Please commit your changes or stash them".** This happens when you edited a notebook that the teacher has moved or updated. Your answers are not lost. Run:

```bash
git stash
git pull
git stash pop
```

`git stash` puts your changes aside, `git pull` gets the new version, and `git stash pop` puts your changes back, even if the notebook has moved to a new folder.

---

## Troubleshooting

**`python` is not recognized (Windows).**
Try `py -m venv .venv` instead of `python -m venv .venv`. If this also fails, Python is not installed:
install it from [python.org](https://www.python.org/downloads/) and tick *Add Python to PATH* during installation.

**PowerShell refuses to run `activate` ("running scripts is disabled").**
Use the *Command Prompt* (`cmd`) instead. If you really want PowerShell, run once:
`Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, then `.venv\Scripts\Activate.ps1`.

**The first cell says the notebook is NOT running inside a virtual environment.**
Jupyter was started from another Python. Close Jupyter, open a terminal, go to the `ml-labs` folder,
activate `.venv` (Step 3), then run `jupyter notebook` again from this terminal.
In VS Code, select the `.venv` kernel again.

**`FileNotFoundError: data/...` when loading a dataset.**
The notebook does not run from its own folder. In VS Code, keep the default setting *Jupyter: Notebook File Root* (`${fileDirname}`).
In the browser, open the notebook from its folder in the Jupyter file list.

**`Failed building wheel for argon2-cffi-bindings` when installing `notebook` (macOS).**
This package has no ready-made version for some Macs, so `pip` tries to compile it and fails.
The simplest fix is to use VS Code (Option A), which does not need it.
If you want Jupyter in the browser, install an older version of the package first:
`pip install "argon2-cffi-bindings<26"`, then `pip install notebook`.

**`ModuleNotFoundError: No module named 'sklearn'` (or `numpy`, `pandas`, ...).**
The packages are not installed in the active environment. Activate `.venv`, then run
`pip install -r requirements.txt` again.

**`xgboost` fails to load (`XGBoostError`, `libomp.dylib` not found) on macOS.**
XGBoost needs the OpenMP library, which macOS does not provide. Install it with Homebrew: `brew install libomp`,
then restart the notebook kernel. On Windows, the same error is fixed by installing the
*Microsoft Visual C++ Redistributable*.

**I use Anaconda.**
Run `conda deactivate` first (until `(base)` disappears from your prompt), then follow the steps above.
Make sure that `(.venv)` appears in the prompt before running `pip install`.

---

## Contents of the repository

| Path | Content |
|---|---|
| `lab1-regression/lab_regression.ipynb` | Lab 1 notebook |
| `lab2-svm-knn/lab_svm_knn.ipynb` | Lab 2 notebook |
| `lab2-svm-knn/data/` | datasets of Lab 2: `data1.txt`, `data2.txt`, and `mpg.csv` (UCI Auto MPG dataset) |
| `lab3-ensembles/lab_ensembles.ipynb` | Lab 3 notebook |
| `lab3-ensembles/data/` | dataset of Lab 3: `covertype.csv` (Forest Cover Type dataset, Kaggle version) |
| `requirements.txt` | the packages to install, for all the labs |
| `.gitignore` | files that Git must ignore (for example the `.venv` folder and the solutions) |
