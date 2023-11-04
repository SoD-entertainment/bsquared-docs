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

## SQLite

> `An error occurred: Incorrect number of bindings supplied. The current statement uses 1, and there are 6 supplied.`

`executemany` expects a list of tuples as its second argument.

BAD

```python
            # Populate access_levels table
            cur.executemany(
                """
                INSERT INTO access_levels (access_level) VALUES (?);
                """,
                [
                    ("banned"),
                    ("bot"),
                    ("viewer"),
                    ("vip"),
                    ("sub"),
                    ("mod"),
                    ("broadcaster"),
                ],
            )
```

NOT BAD

```python
            # Populate access_levels table
            cur.executemany(
                """
                INSERT INTO access_levels (access_level) VALUES (?);
                """,
                [
                    ("banned",),    👈👈 Note added commas
                    ("bot",),
                    ("viewer",),
                    ("vip",),
                    ("sub",),
                    ("mod",),
                    ("broadcaster",),
                ],
            )
```

---

## OOP

BAD

> `An error occurred: Call parameter is not a request object`

This is because it's expecting an object.

```py
def send_request(self, request):
    response = self.ws.call(getattr(requests, request))    # problem
```

NOT BAD

Create an `instance`

```py
def send_request(self, request, *args, **kwargs):
    request_class = getattr(requests, request)
    request_instance = request_class(*args, **kwargs)
    response = self.ws.call(request_instance)
```
