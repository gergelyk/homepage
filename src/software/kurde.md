# kurde

Simple configuration language, based on Python.

## Features

- Python syntax
- Flexible Enums
- Easily created nested dictionaries
- Direct addess to environment variables
- Calling/capturing shell commands
- Path manipulation
- Module `re` immediately available

## Example

```python
# Enum from `simple-enum` package is available.
# By default enum items are serialized by names.
class Color(Enum):
    red
    green
    blue
    white
    black

# Alternatively, enum items can be replaced by numbers assigned automatically.
class Priority(Enum, values=enum.from_zero):
    low
    medium
    high

# In the simple cases, standard dictionary is sufficient.
# It is serialized as JSON object.
theme = dict(
    foreground = Color.black,
    background = Color.green,
)

# Dictionary can be also created by assigning the the attributes.
# Dict comes from `addicts` package.
user = Dict()

# Environment variables can be accessed directly.
user.name = env.USER or 'admin'
user.full_name = "Tom Brown"

# Module re immediately available.
user.last_name = re.findall('[^ ]+', user.full_name)[-1]

# lists, dicts, sets are serialized as JSON arrays.
user.aliases = ('tommy', 'tbrown', 'brown')
user.nick = None

network = Dict()

# Non-existing attributes are created on the fly.
network.local.priority = Priority.medium

# Shell commands can be easily invoked.
# Behind `cmd` we get `plumbum.local.cmd`.
network.local.name = cmd.hostname().strip()

# pathlib.Path immediately available.
network.local.cert_path = Path(__file__).parent.absolute() / 'cert.pem'

# Closures and other constructs available.
network.remotes = {f"proxy{n}": f'192.168.0.{100 + n}' for n in range(3)}
network.remotes['localhost'] = '127.0.0.1'
```

Renders as:
```json
{
  "theme": {
    "foreground": "black",
    "background": "green"
  },
  "user": {
    "name": "kendo",
    "full_name": "Tom Brown",
    "last_name": "Brown",
    "aliases": [
      "tommy",
      "tbrown",
      "brown"
    ],
    "nick": null
  },
  "network": {
    "local": {
      "priority": 1,
      "name": "precision",
      "cert_path": "/home/kendo/wrk/kurde/examples/cert.pem"
    },
    "remotes": {
      "proxy0": "192.168.0.100",
      "proxy1": "192.168.0.101",
      "proxy2": "192.168.0.102",
      "localhost": "127.0.0.1"
    }
  }
}
```

## Disclaimer

Kurde doesn't do any sandboxing. Invoke the scripts only if you absolutely trust them. You are doing it on your own responsibility.
