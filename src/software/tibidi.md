# tibidi

<p align="right">
<a href="https://gergelyk.github.io/python-tibidi/"><img src="/assets/book.svg"/></a>
<a href="https://github.com/gergelyk/python-tibidi/"><img src="/assets/github.svg"/></a>
<a href="https://pypi.org/project/tibidi/"><img src="/assets/package.svg"/></a>
</p>

Post-mortem debugging for Python. Dump your traceback into a file. Analyzer it later.

## Example

```python
import sys
import tibidi
tibidi.set_excepthook()

def div(x, y):
    return x / y

if __name__ == '__main__':
    x = int(sys.argv[1])
    y = int(sys.argv[2])
    print(div(x, y))
```

```sh
$ python3 divide.py 5 0
ZeroDivisionError: division by zero
Traceback dumped into: traceback.pkl
$ python3 -m tbpeep traceback.pkl
```

<img src="https://gergelyk.github.io/python-tibidi/assets/peep1.png"/>
<img src="https://gergelyk.github.io/python-tibidi/assets/peep2.png"/>
<img src="https://gergelyk.github.io/python-tibidi/assets/peep3.png"/>
<img src="https://gergelyk.github.io/python-tibidi/assets/peep4.png"/>



More examples can be found in the [documentation](https://gergelyk.github.io/python-tibidi/).
