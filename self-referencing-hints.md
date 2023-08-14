## Self-Referencing Type Hints

Inside of a class, if you write a type hint that refers to the same class Python will raise an Error because the class is not known yet.   
For example:
```python
class Money:
    def __add__(self, other: Money) -> Money:  # ERROR: Money is unknown
        """Return the sum of two money objects."""
        ... (code omitted)
```

to fix this, add the following import:
```python
from __future__ import annotations

class Money:
    def __add__(self, other: Money) -> Money:  # OK!
```