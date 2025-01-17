# prevcurrnext

Iteration utils for "prev", "curr", and "next"-style for-loops.

## Install

```bash
pip install prevcurrnext
```

## Usage

The `prevcurrnext` function yields pairs of consecutive elements from an iterable, allowing you to see the "previous", "current", and "next" items for each element. It includes options to yield `None` at the beginning and/or end of the sequence for convenient boundary handling.

```python
from prevcurrnext import prevcurr, currnext, prevcurrnext

# Basic usage
for prev, curr in prevcurr([1, 2, 3]):
    print(prev, curr)
# Output:
# None 1
# 1 2
# 2 3

# Customizing boundary behavior
# Adding None at the end
for prev, curr in prevcurr([1, 2, 3], end_curr_on_none=True):
    print(prev, curr)
# Output:
# None 1
# 1 2
# 2 3
# 3 None

for curr, _next in currnext([1, 2, 3]):
    print(curr, _next)
# Output:
# 1 2
# 2 3
# 3 None

for prev, curr, _next in prevcurrnext([1, 2, 3]):
    print(prev, curr, _next)
# Output:
# None 1 2
# 1 2 3
# 2 3 None
```

### Available functions

* **`currprev`**
* **`prevcurr`**
* **`currnext`**
* **`nextcurr`**
* **`prevcurrnext`**
* **`nextcurrprev`**

All functions have nearly the exact same parameters:

- **`iterable`**: The iterable to process.
- **`start_prev_on_none`**: Whether to yield `None` for the "previous" item before the first element. Default is `True`.
- **`end_curr_on_none`**: Whether to yield `None` for the "current" item after the last element. Default is `False`.
- **`end_next_on_none`**: Whether to yield `None` for the "next" item after the last element. Default is `True`.

## Contributing

Contributions are welcome! If you find issues or have suggestions, please open an issue or submit a pull request on [GitHub](https://github.com/yourusername/prevcurr).

## Development Setup

#### If you use [Poetry](https://python-poetry.org/)

```bash
poetry install
poetry run pytest
```

#### Otherwise...

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements-dev.txt
pip install -e .
pytest
```

## License

This project is licensed under the [MIT License](LICENSE).
