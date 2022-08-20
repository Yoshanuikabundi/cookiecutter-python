# Compiling {{cookiecutter.project_name}}'s Documentation

The docs for this project are built with [Sphinx](http://www.sphinx-doc.org/en/master/).

{% if (cookiecutter.dependency_source == 'Prefer conda-forge over the default anaconda channel with pip fallback' or cookiecutter.dependency_source == 'Prefer default anaconda channel with pip fallback') %}
To compile the docs, first install the dependencies into a new conda environment, and then compile the documentation from that environment.
```bash
conda env create --file devtools/conda-envs/docs_env.yaml --name {{cookiecutter.repo_name}}_docs
conda activate {{cookiecutter.repo_name}}_docs
sphinx-build -b html -j auto docs docs/_build/html
```
The compiled docs will be in `docs/_build/html` and can be viewed by opening `index.html` in a browser.
{% elif cookiecutter.dependency_source == 'Dependencies from pip only (no conda)' %}
To compile the docs, first ensure that Sphinx and the ReadTheDocs theme are installed.
```bash
pip install sphinx sphinx_rtd_theme
```

Once installed, you can use the `Makefile` in this directory to compile static HTML pages by
```bash
make html
```

The compiled docs will be in the `_build` directory and can be viewed by opening `index.html` (which may itself 
be inside a directory called `html/` depending on what version of Sphinx is installed).
{% endif %}

{% if (cookiecutter.include_ReadTheDocs == 'y') %}
A configuration file for [Read The Docs](https://readthedocs.org/) (readthedocs.yaml) is included in the top level of the repository. To use Read the Docs to host your documentation, go to https://readthedocs.org/ and connect this repository. You may need to change your default branch to `main` under Advanced Settings for the project.

If you would like to use Sphinx's automatic API documentation generation and your package has dependencies, you will need to include those dependencies in your documentation yaml file (`devtools/conda-envs/test_env.yaml`).

{% endif %}