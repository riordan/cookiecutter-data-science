# Cookiecutter Data Science: Dockerized VSCode Edition

_A logical, reasonably standardized, but flexible project structure for doing, collaborating on, and sharing data science work._

Derived from [Cookiecutter Data Science](http://drivendata.github.io/cookiecutter-data-science/)


## Installation

_Note: This was developed with the expectation of being used on Mac OS, though it should work just fine on other environments (with slightly different instructions)._

This template relies on the following tools:
- python
- [pipx](https://pypa.github.io/pipx/)
- cookiecutter
- [Docker](https://docs.docker.com/get-docker/)
- Visual Studio Code

Additionally, [Homebrew](https://brew.sh) will be used to install and configure all the other tools we'll be using. Feel free to skip any you already have installed.

### Prerequisite Configuration (Mac)

**0. Install [Homebrew](http://brew.sh)**

```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**1. Install Docker**
Docker allows us to run a virtualized environment for local development. It's a computer inside your computer.
```bash
$ brew install --cask docker
```

**2. Install VSCode**
Visual Studio Code (aka `vscode`) is a modern, open-source text editor from Microsoft(‽). Through its extensive plug-ins, it also makes for a powerful environment for collaborative Jupyter notebook development.
```bash
$ brew install --cask visual-studio-code
```


**3. Install pipx**
[pipx](https://pypa.github.io/pipx/) creates isolated python environments for Python-based CLI tools. It makes it harder to break standalone tools that rely on Python, even if your main developer environment goes haywire.

```bash
$ brew install pipx
```

**4. Use pipx to install Cookiecutter**
[Cookiecutter](https://cookiecutter.readthedocs.io) is a Python CLI tool used to create standard project templates. We use it to scaffold our data science project.

```bash
$ pipx install cookiecutter
```

*phew: you're done with pre-setup*

### To start a new project, run:
------------

    cookiecutter -c vscode https://github.com/riordan/cookiecutter-data-science


[![asciicast](https://asciinema.org/a/244658.svg)](https://asciinema.org/a/244658)


### The resulting directory structure
------------

The directory structure of your new project looks like this: 

```
├── LICENSE
├── Makefile           <- Makefile with commands like `make data` or `make train`
├── README.md          <- The top-level README for developers using this project.
├── data
│   ├── external       <- Data from third party sources.
│   ├── interim        <- Intermediate data that has been transformed.
│   ├── processed      <- The final, canonical data sets for modeling.
│   └── raw            <- The original, immutable data dump.
│
├── docs               <- A default Sphinx project; see sphinx-doc.org for details
│
├── models             <- Trained and serialized models, model predictions, or model summaries
│
├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
│                         the creator's initials, and a short `-` delimited description, e.g.
│                         `1.0-jqp-initial-data-exploration`.
│
├── references         <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures        <- Generated graphics and figures to be used in reporting
│
├── requirements.txt   <- The requirements file for reproducing the analysis environment, e.g.
│                         generated with `pip freeze > requirements.txt`
│
├── setup.py           <- makes project pip installable (pip install -e .) so src can be imported
├── src                <- Source code for use in this project.
│   ├── __init__.py    <- Makes src a Python module
│   │
│   ├── data           <- Scripts to download or generate data
│   │   └── make_dataset.py
│   │
│   ├── features       <- Scripts to turn raw data into features for modeling
│   │   └── build_features.py
│   │
│   ├── models         <- Scripts to train models and then use trained models to make
│   │   │                 predictions
│   │   ├── predict_model.py
│   │   └── train_model.py
│   │
│   └── visualization  <- Scripts to create exploratory and results oriented visualizations
│       └── visualize.py
│
└── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io
```
