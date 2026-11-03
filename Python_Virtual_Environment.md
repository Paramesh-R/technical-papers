# Python Virtual Environment

### What is Python Virtual Environment?

A Python virtual environment is an isolated environment that allows us to install and manage Python packages separately for each project.

Normally, Python packages are installed globally on the system. This means multiple projects may use the same packages and package versions.

This can create conflicts when different projects require different versions of the same package.

---

#### Example:

- Project A required Django 4.2
- Project B required Django 5.1

### What is venv?

venv is a buillt-in python module used to create virtual environments. It is available in Python 3.3 and later.

---

**Syntax:** `python3 -m venv environment_name`

Explanation:

- python3: Python interpreter.
- -m: Executes a Python module as a script.
- venv: Python module responsible for creating virtual environments.
- environment_name: Name of the virtual environment directory

---

### Creating a Virtual Environment:

```
mkdir my_project

cd my_project

python3 -m venv .venv

source .venv/bin/activate

deactivate
```

---

### Requirements File

requirement.txt is a text file that stores the dependencies required by a python project.
It helps other developers install the same packages used in your project.

**Create Requirements File:**

```
pip freeze > requirements.txt
```

**Install Dependencies from requirements.txt**

```
pip install -r requirements
```

-r: read the requirements from a file

**Removing a Virtual Environment:**

```
deactivate

rm -rf .venv
```

## Using a Virtual Environment with Git

A Virtual environment should not normally be uploaded to Github or GitLab.

**Why?:**

- It contains many installed files
- It can consume significant disk space
- It may contain platform-specific executables
- Other developers can recreate it using **requirements.txt**

Add .venv/ to your .gitIgnore file:

```
# Python virtual environment
.venv/
venv/
env/

# Python cache
__pycache__/
*.pyc

# Environment variables
.env

# IDE settings
.vscode/
.idea/

# Generated plots
plots/
```

---

## Practical Workflow

```
# 1. Create project directory
mkdir python_project

# 2. Navigate into project
cd python_project

# 3. Create virtual environment
python3 -m venv .venv

# 4. Activate virtual environment
source .venv/bin/activate

# 5. Upgrade pip
python -m pip install --upgrade pip

# 6. Install dependencies
pip install pandas numpy matplotlib

# 7. Generate requirements file
pip freeze > requirements.txt

# 8. Create Python file
touch main.py

# 9. Execute Python file
python main.py

# 10. Deactivate environment
deactivate
```
