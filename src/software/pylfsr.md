# pylfsr

<p align="right">
<a href="https://pylfsr.readthedocs.io/en/latest/"><img src="/assets/book.svg"/></a>
<a href="https://github.com/gergelyk/pylfsr"><img src="/assets/github.svg"/></a>
<a href="https://pypi.org/project/lfsr/"><img src="/assets/package.svg"/></a>
</p>

[Linear-Feedback Shift Registers](https://en.wikipedia.org/wiki/Linear-feedback_shift_register) are components widely used in digital electronics. This is a toolkit for designing them.

It supports LFSR with internal feedback (Galois implementation) and with external feedback (Fibonacci implementation).

## Example

LFSR with internal feedback described by polynomial `x**3+x**2+1`, encode as `0x0D` with initial value of `0x01` would look like:

```
+----<-----+-------<-------+
|          |               |
+-----[0]-XOR-[0]-----[1]--+-->-- out

x**3     x**2    x**1    x**0
```

Values at its output can be check by:

```python
>>> n = 3
>>> taps = max_len_lfsr_min_taps[n]
>>> poly = taps_to_poly(taps)
>>> prng = lfsr_if(poly)
>>> for i in range(10):
...     print(i, next(prng))
0 1
1 6
2 3
3 7
4 5
5 4
6 2
7 1
8 6
9 3
```

More details and examples can be found in the [documentation](https://pylfsr.readthedocs.io/en/latest/).
