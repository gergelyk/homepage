# digitout

<p align="right">
<a href="https://gergelyk.github.io/python-digitout/"><img src="/assets/book.svg"/></a>
<a href="https://github.com/gergelyk/python-digitout"><img src="/assets/github.svg"/></a>
<a href="https://pypi.org/project/digitout/"><img src="/assets/package.svg"/></a>
</p>

Seek data structures of your Python application.

## Example

Given following code:

```python
def foobar() -> 123:
    pass
```

How can we access `123` starting from object `foobar`?

```python
...
import digitout
digitout(foobar) # shows interactive UI
```

![](https://raw.githubusercontent.com/gergelyk/python-digitout/master/docs/assets/demo.gif)


Shortest answer:

```python
target.__annotations__['return']: 123
```
