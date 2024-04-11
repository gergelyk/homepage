# para-cada

<p align="right">
<a href="https://gergelyk.github.io/para-cada/"><img src="/assets/book.svg"/></a>
<a href="https://github.com/gergelyk/para-cada"><img src="/assets/github.svg"/></a>
<a href="https://pypi.org/project/para-cada/"><img src="/assets/package.svg"/></a>
</p>

*Para Cada* in Spanish means *For Each*. The tool executes your command for each file selected using glob expression(s).

Why? Let's say you have multiple `.tgz` archives and you would like to extract them in one shot. Some of the options available in bash are:

```sh
ls *.tgz | xargs -IT tar xzvf T
for T in *.tgz; do tar xzvf $T; done
find . -type f -name '*.tgz' -exec tar xzvf {} \;
```

All of them are relatively complex. This is where cada can help. Simply do:

```sh
cada 'tar xzvf *.tgz'
```

![](https://raw.githubusercontent.com/gergelyk/para-cada/master/docs/assets/images/example.png)

Cada knows where glob expression is. It executes entire command with subsequent values corresponding to this expression. Additionally, user may transform/filter/sort those values using regular Python syntax. Take a look at the [documentation](https://gergelyk.github.io/para-cada/).
