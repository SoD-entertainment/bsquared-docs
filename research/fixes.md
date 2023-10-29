# Errors and Fixes Documentation

Issues I've encountered (mostly due to learning Python while doing this project) and how I managed to fix them.

## Linting

> `Do not use bare except`

BAD

```python
def connect(self):
    try:
        self.ws.connect()
    except:        # 👈👈👈 ERROR
        print("Failed to connect to OBS")
```

NOT BAD

```python
def connect(self):
    try:
        self.ws.connect()
    except Exception as e:        # 👈👈👈 FIX
        print(f"Failed to connect to OBS: {e}")       # ENSURE f-string
```

---
