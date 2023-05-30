# Home

Material for MkDocs is used to document the important details of the CloudLabs project, including API and other technical specifications.
For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Setup

### Python
1. Install build dependencies, which are required to install Python via `pyenv`
```bash
sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```
2. Install the latest version of Python, in which the Python version manager, [pyenv](https://github.com/pyenv/pyenv) may be used:
```bash
# Install the latest version of Python 3.11
pyenv install 3.11
```
3. Configure and set the appropriate Python version
```bash
# List installed version
pyenv versions

# Set a Python version system-wide
pyenv 3.11.3
```

### Project
1. Git clone the repository and initialize a Python virtual environment within the directory:
```bash
# Clone the repository via SSH
git clone git@github.com:projectcatena/cloudlabs-mkdocs.git

# Init a Python virtual environment
python -m venv env

# Activate the Python venv
source env/bin/activate
```
2. Install the `mkdocs-material` python package:
```bash
pip install mkdocs-material
```
3. The project may be deployed locally by running the following commands:
```bash
# Start the live-reloading docs server
mkdocs serve
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
