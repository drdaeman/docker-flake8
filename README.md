Docker image for Python 3 and Flake8
====================================

This image is meant to be used to quickly check if code is alright.
My use case is automated CI runs.

[![Docker Build Status][badge]](https://hub.docker.com/r/drdaeman/flake8/)

What's included
---------------

- Python 3.x (latest), as the image is based on `python:3-alpine`
- Flake8 with the following plugins (latest versions, as available
    on PyPI at image build time):
  - flake8-comprehensions
  - flake8-docstrings
  - flake8-import-order
  - flake8-mutable
  - flake8-pep3101
  - flake8-pyi
  - flake8-quotes
  - flake8-string-format
  - pep8-naming
- Image is configured to run as a non-privileged (non-root) user.
- Some default flake8 settings that I prefer, like double quotes and
  120-column margins. YMMV, override those in your own `.flake` file.

Usage
-----

Image is pre-configured to have `flake8` as its entryppoint and
starts in `/project` (empty, bind-mount your code in there).

So, assuming your code is world-readable, to lint your files,
all you have to run is:

    docker -it --rm -v $(pwd):/project drdaeman/flake8


[badge]: https://img.shields.io/docker/build/drdaeman/flake8.svg
