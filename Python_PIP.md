# Python - PIP

What is PIP?

PIP stands for Pip Installs Packages (recursive acronym).

It is the standard package installer for Python.

It allows developers to install, upgrade, uninstall and manage third-party Python packages.

Examples of Python packages:

- numpy – Numerical computing.
- pandas – Data manipulation and analysis.
- matplotlib – Data visualization.

Example:
`pip install pandas`

This command downloads and installs the pandas package and its required dependencies.

---

Check whether pip is installed:
`pip --version`

Alternative:
`python3 -m pip --version`

Check the pip executable location:
`which pip`

Check Python version:
`python --version`

Check Python executable location:
`**which python**`

---

Installing Packages
|Install a package:| pip install pandas|
|------------------|---------------------|
|Install multiple packages:|pip install numpy pandas matplotlib|
|Install a specific version:|pip install pandas==2.2.3|
|Install a minimum version:|pip install "pandas>=2.2"|
|Install a version within a range:|pip install "pandas>=2.2,<3.0"|
|Install the latest available compatible version:|pip install --upgrade pandas|
|Install without displaying progress:|pip install --quiet pandas|
|Install without using pip cache:|pip install --no-cache-dir pandas|

| Task          | Command                                           |
| ------------- | ------------------------------------------------- |
| Check         | pip version pip --version                         |
| Install       | package pip install pandas                        |
| Install       | multiple packages pip install numpy pandas        |
| Install       | specific version pip install pandas==2.2.3        |
| Upgrade       | package pip install -U pandas                     |
| Upgrade       | pip python -m pip install --upgrade pip           |
| Uninstall     | package pip uninstall pandas                      |
| List          | packages pip list                                 |
| List          | outdated packages pip list --outdated             |
| Package       | information pip show pandas                       |
| Export        | dependencies pip freeze > requirements.txt        |
| Install       | requirements pip install -r requirements.txt      |
| Check         | dependencies pip check                            |
| Display       | cache pip cache info                              |
| Clear         | cache pip cache purge                             |
| Download      | package pip download pandas                       |
| Install       | from GitHub pip install git+URL                   |
| Install       | without dependencies pip install --no-deps pandas |
| Force         | reinstall pip install --force-reinstall pandas    |
| Search        | available versions pip index versions pandas      |
| Configuration | pip config list                                   |
