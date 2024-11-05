# bkp

<p align="right">
<a href="https://github.com/gergelyk/x-strings"><img src="/assets/github.svg"/></a>
<a href="https://pypi.python.org/pypi/x-strings"><img src="/assets/package.svg"/></a>
</p>

Extend Python syntax by defining custom string prefix. Provide function that transforms strings with your prefix.

This corresponds to Tagged Template Literals feature in JavaScript.

This project is only a toy. Technique used here shouldn't be considered as a good coding practice due to the fact how it is implemented. I don't recommend using it in production code. Hopefully it can be inspiring though.

## Features

- Multiple encodings can be defined
- Multiple prefixes can be defined
- Prefixes can have more that one letter
- Encodings can take arguments (captured by regex)
- Doesn't corrupt Python syntax-error messages

## Examples

Simple example is shown below. More advanced examples can be found in [here](https://github.com/gergelyk/xstrings/tree/master/examples).

`app.py`:

```python
# coding: x-strings
print(x"Hello World")
```

`launcher.py`:

```python
import xstrings
xstrings.register({'x': lambda t: t + "!!!"})

import app
```

Notice exclamation marks added to the end of the message:
```sh
$ python3 launcher.py
Hello World!!!
```
