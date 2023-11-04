# Schtuff I Learnt

## Python

## getattr()

> **getattr(object, name, default)**
> Return the value of the named attribute of object. name must be a string. If the string is the name of one of the object’s attributes, the result is the value of that attribute. For example, getattr(x, 'foobar') is equivalent to x.foobar.

```python
def send_request(self, request_var):
    response = self.ws.call(getattr(requests, request))   # equiv requests.request_var
```

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

When running scripts, the PYTHONPATH needs to be set (to the parent directory of the src folder):

1. cd into the parent directory
2. `set PYTHONPATH=%cd%`
3. Run the module: `py -m src.folder.folder.script` (make sure there's no `.py` extension)
4. **ENSURE ALL IMPORTS ARE THEN `from src.folder.folder.script import blah_function`**

## Instances

In python, instances are akin to javascript classes. You create an instance by calling a class as if it were a function.

```python
class MyClass:              # The class
    def __init__(self, value):
        self.value = value

my_instance = MyClass(5)     # The instance of MyClass with the PROPERTY 'value'
```

In JS, we're looking at this:

```javascript
class MyClass {
  constructor(value) {
    this.value = value;
  }
}

const myInstance = new MyClass(5);
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

- [obsws-python](https://pypi.org/project/obsws-python/) ❓
- [obs-websocket-py](https://github.com/Elektordi/obs-websocket-py) 👈

---

## General Learnings

- [TOML (like YAML)](https://toml.io/en/)
