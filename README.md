# Const Protocols

This module contains a set of "const" protocols for python modules. You can
use these along with function parameters to have your static type checker
(mypy, for example) catch cases of mutation you don't exepct.

For example:

```python
def uses_list(value: ConstList[str]) -> str:
    value.append('bar')  # Error! value does not have append method!
```

The underlying python values have not actually become immutable, but like C
and C++ it's more of a promise that if you take a ConstList or return one
that you're not going to modify the thing.