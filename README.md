## Configuration

### Local configuration

A file named `.borg.toml` should exist in the directory where `borg` is run.
This configuration file tells `borg` where to find the templates to compare
the local directory to.

See `.borg.toml` in this directory for an example.

URL should point to a web directory containing a `.borg.template.toml` file and all expected files specified in that file.

An expected use case is using `raw.githubusercontent` URLs for public GitHub repositories.

```
[source]
url = 'https://github.com/techservicesillinois/secdev-template-python/blob/main/'
```

Other GitHub branches can also be used for comparison, using a `refs/heads` URL:

```
[source]
# Use an un-merged `doc/python` branch:
url = 'https://github.com/techservicesillinois/secdev-template-python/refs/heads/doc/python'  # Open Pull Request
```

> Note: Our typical use case is public templates. But a private repository can be used, by first cloning it, and then calling `borg` with `--source-dir`.


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

No endpoints. The outputs of this this tool are managed through a separate dedicated tool, such as `git`.

