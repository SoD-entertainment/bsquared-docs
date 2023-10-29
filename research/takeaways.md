# Schtuff I Learnt

## Python

## requirements.txt

Multiple packages can be installed (i.e. equiv of `npm i` / `package.json`) with a `requirements.txt` file in the `root` of the project.

```bash
pip install -r requirements.txt
```

Updating requirements when adding new packages can be done automatically. This will populate `requirements.txt` with **all** packages (and their versions) currently installed on the system:

```bash
# Obv this should be done in venv
pip freeze > requirements.txt
```

### Modularising an app

In order to import modules using package syntax, you need to create an empty `__init__.py` file in each folder & subfolder.

If you need to set up package-wide state, or provide convenient access to a deeply nested function/class, you can whack this in:

```python
# __init__.py
from .some_subpackage.some_module import some_function as package_level_function
```

_Then, you can access `some_function` with:_

```python
import my_package

my_package.package_level_function()
```

---

## python_dotenv

**REF:** [here](https://pypi.org/project/python-dotenv/#getting-started)

- `os.environ` vs `os.getenv`: [SO post](https://stackoverflow.com/questions/16924471/difference-between-os-getenv-and-os-environ-get)

---

## PyQt

**REF**: [here](https://realpython.com/python-pyqt-gui-calculator/#installing-pyqt)

---

## OBS connection

- [TOML (like YAML)](https://toml.io/en/)
- [obsws-python](https://pypi.org/project/obsws-python/) ❓
- [obs-websocket-py](https://github.com/Elektordi/obs-websocket-py) 👈
