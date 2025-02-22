# ![voila](docs/source/voila-logo.svg)

[![Documentation](http://readthedocs.org/projects/voila/badge/?version=latest)](https://voila.readthedocs.io/en/latest/?badge=latest)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/QuantStack/voila/stable?urlpath=voila%2Ftree%2Fnotebooks)
[![Join the Gitter Chat](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/QuantStack/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Rendering of live Jupyter notebooks with interactive widgets.

## Introduction

Voila serves live Jupyter notebooks including Jupyter interactive widgets.

Unlike the usual HTML-converted notebooks, each user connecting to the Voila
tornado application gets a dedicated Jupyter kernel which can execute the
callbacks to changes in Jupyter interactive widgets.

- By default, voila disallows execute requests from the front-end, preventing
  execution of arbitrary code.
- By default, voila runs with the `strip_source` option, which strips out the
  input cells from the rendered notebook.

## Installation

Voila can be installed with the conda package manager

```
conda install -c conda-forge voila
```

or from pypi

```
pip install voila
```

### JupyterLab preview extension

Voila provides a JupyterLab extension that displays a Voila preview of your Notebook in a side-pane:

```
jupyter labextension install @jupyter-voila/jupyterlab-preview
```

## Usage

### As a standalone tornado application

To render the `bqplot` example notebook as a standalone app, run
`voila bqplot.ipynb`.
To serve a directory of jupyter notebooks, run `voila` with no argument.

For example, to render the example notebook `bqplot.ipynb` from this repository with voila, you can first update your current environment with the requirements of this notebook (in this case in a [conda environment](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) and render the notebook with

```
conda env update -f environment.yml
cd notebooks/
voila bqplot.ipynb
```

For more command line options (e.g., to specify an alternate port number),
run `voila --help`.

### As a server extension to `notebook` or `jupyter_server`

Voila can also be used as a notebook server extension, both with the
[notebook](https://github.com/jupyter/notebook) server or with
[jupyter_server](https://github.com/jupyter/jupyter_server).

To install the notebook server extension, run

```
jupyter serverextension enable voila --sys-prefix
```

When running the notebook server, the voila app is accessible from the base url
suffixed with `voila`.

## Documentation

To get started with using Voila, check out the full documentation:

https://voila.readthedocs.io/

## Examples

The following two examples show how a standalone Jupyter notebook can be turned into a separate app, from the command-line integration.

**Rendering a notebook including interactive widgets and rich mime-type rendering**
![voila basics](voila-basics.gif)

**Rendering a notebook making use of a custom widget library ([bqplot](https://github.com/bloomberg/bqplot))**

![voila bqplot](voila-bqplot.gif)

**Showing the source code for a voila notebook**

The sources of the Jupyter notebook can be displayed in a voila app if option `strip_sources` is set to `False`.

![voila sources](voila-sources.gif)

**Voila dashboards with other language kernels**

Voila is built upon Jupyter standard formats and protocols, and is agnostic to the programming language of the notebook. In this example, we present an example of a voila application powered by the C++ Jupyter kernel [xeus-cling](https://github.com/QuantStack/xeus-cling), and the [xleaflet](https://github.com/QuantStack/xleaflet) project.

![voila cling](voila-cling.gif)

## Voila Gallery

The [Voila Gallery](https://voila-gallery.org) is a collection of live dashboards and applications built with Voila and Jupyter widgets.

Most of the examples rely on widget libraries such as ipywidgets, ipyleaflet, ipyvolume, bqplot and ipympl, and showcase how to build complex web applications entirely based on notebooks.

New examples can be added to the gallery by following the steps listed in the [voila-gallery/gallery](https://github.com/voila-gallery/gallery) repository.

## Development

See [CONTRIBUTING.md](./CONTRIBUTING.md) to know how to contribute and setup a development environment.

## Related projects

Voila depends on [nbconvert](https://github.com/jupyter/nbconvert) and
[jupyter_server](https://github.com/jupyter/jupyter_server/).

## License

We use a shared copyright model that enables all contributors to maintain the
copyright on their contributions.

This software is licensed under the BSD-3-Clause license. See the
[LICENSE](LICENSE) file for details.
