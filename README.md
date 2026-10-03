# Lab: From Linear Regression to Inverse Problems

Master Smart Data, ENSAI · Machine Learning lab (2 hours)

In this lab, you will fit linear and logistic regression models, regularize them with Ridge,
and use the same tools to recover a sharp image from a blurry one.

Before the lab, you need to set up your working environment. Follow the steps below **in order**.
It takes about 10 minutes.

---

## Why a virtual environment?

A **virtual environment** (venv) is a private folder that contains its own Python packages.
Each project gets its own environment, so:

* the packages of this lab do not interfere with your other projects,
* anyone can rebuild exactly the same environment from the file `requirements.txt`.

This is standard practice for any Python project, in research as in industry.

---

## Step 1. Get the lab on your machine

Open a terminal.

Move to the folder where you keep your courses, for example:

```bash
cd Documents
```

Then download the repository with Git:

```bash
git clone https://github.com/thibault-pautrel/lab-regression.git
cd lab-regression
```

**No Git on your machine?** On the GitHub page of the repository, click the green **Code** button,
then **Download ZIP**. Unzip the folder, then move into it with `cd` in your terminal.

Check that you are in the right folder: the command `dir` (Windows) or `ls` (macOS, Linux)
must list `README.md`, `requirements.txt` and `lab_regression.ipynb`.

## Step 2. Create the virtual environment

```bash
python -m venv .venv
```

This creates a folder `.venv` inside the lab folder. On macOS and Linux, if `python` is not found, use `python3`.

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

This installs `numpy`, `matplotlib`, `scikit-learn` and Jupyter **inside** `.venv` only.

## Step 5. Open the notebook

**Option A: Jupyter in the browser.** From the same terminal, with `(.venv)` active:

```bash
jupyter notebook
```

A browser tab opens. Click on `lab_regression.ipynb`.

**Option B: VS Code.** Open the lab folder in VS Code (*File > Open Folder*), open `lab_regression.ipynb`,
click on *Select Kernel* at the top right, and choose the interpreter located in `.venv`.

## Step 6. Check your installation

Run the first code cell of the notebook (Part 0). It must print `Environment OK`.
You are ready.

---

## Troubleshooting

**The first cell says the notebook is NOT running inside a virtual environment.**
Jupyter was started from another Python. Close Jupyter, open a terminal, go to the lab folder,
activate `.venv` (Step 3), then run `jupyter notebook` again from this terminal.
In VS Code, select the `.venv` kernel again.

**`ModuleNotFoundError: No module named 'sklearn'` (or `numpy`, ...).**
The packages are not installed in the active environment. Activate `.venv`, then run
`pip install -r requirements.txt` again.

**I use Anaconda.**
The steps above still work from the *Anaconda Prompt*. Make sure that `(.venv)` appears in the prompt
before running `pip install`.

---

## Contents of the repository

| File | Content |
|---|---|
| `lab_regression.ipynb` | the lab notebook |
| `requirements.txt` | the list of packages to install |
| `.gitignore` | files that Git must ignore (here, the `.venv` folder) |
