# CloudLabs Documentation

Material for MkDocs is used to document the important details of the CloudLabs project, including API and other technical specifications.
For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Setup

Install the latest version of Python, in which the Python version manager, [pyenv](https://github.com/pyenv/pyenv) may be used:
```bash
# Install the latest version of Python 3.11
pyenv install 3.11
```
Git clone the repository and initialize a Python virtual environment within the directory:
```bash
# Clone the repository via SSH
git clone git@github.com:projectcatena/cloudlabs-mkdocs.git

# Init a Python virtual environment
python -m venv env

# Activate the Python venv
source env/bin/activate
```
Install the `mkdocs-material` python package:
```bash
pip install mkdocs-material
```
The project may be deployed locally by running the following commands:
```bash
# Start the live-reloading docs server
mkdocs serve

# or to build the documentation site
mkdocs build
```

<!-- * `mkdocs new [dir-name]` - Create a new project. -->
<!-- * `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit. -->

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
