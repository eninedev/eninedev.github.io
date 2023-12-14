# [Developer Guide](index.md)

## PyLint

> https://www.pylint.org/

### Installation

```
pip install pylint~=3.0
pip install pylint-django~=2.5
```

### Configuration

PyLint configuration can be customized and is looked for in the following places in the order shown:

- `pylintrc --rcfile=<custompylintrc>`
- `<your_project>/pylintrc`
- `~/.pylintrc`
- `/etc/pylintrc`

### Standard File

1E9 Advisors uses the following [pylintrc](pylintrc) file that is available for download.

### Running on a project

```
find . -type f -name '*.py' -exec pylint {} \;
```

