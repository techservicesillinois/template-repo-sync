## Configuration

### Local configuration

A file named `.borg.toml` should exist in the directory where `borg` is run.
This configuration file tells `borg` where to find the templates to compare
the local directory to.

See `.borg.toml` in this directory for an example.

### Template configuration 

The remote `url` should contain a file named `.borg.template.toml`.
This file specifies which of the files available at the remote URL
should be treated as templates for comparison.

Example `.borg.template.toml`:

```
[template]
files = [
    ".gitattributes",
    ".github/workflows/deploy.yml",
    ".gitignore",
    "CODE_OF_CONDUCT.md",
    "Makefile",
    "SECURITY.md",
    "mypy.ini",
    "pyproject.toml",
    "tests/test_python_version.py",
]
```


## Data Sources

|Data Store|Data Type|Sensitivity|Notes|
|----------|---------|-----------|-----|
| Remote template URL | Text | Public | |

## Endpoint Connections

None - Changes made by this tool should be managed through a separate dedicated tool, such as `git`.
