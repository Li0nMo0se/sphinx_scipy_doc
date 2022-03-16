# Sphinx scipy documentation sphinx

## Step by step


1. Copy `docs` folder in your repository (in the folder containing everything related to the documentation)
2. `docs/source/conf.py` is the configuration file (project name, project version, module location, etc...). In this file, **replace variable values** where there is a **FIXME**. Other variables values can be modified to customize the documentation generation (no explanation will be given here).
3. Build the docker image: `docker build -t mysphinx-latexpdf -f docs/Dockerfile`. That docker image contains all the required dependencies for sphinx.
4. Create reStructuredText module configuration using the built image: `docker run --rm -v /home/li0nmo0se/project/sphinx_scipy_doc/:/docs mysphinx-latexpdf sphinx-apidoc -f -o ./docs/source  my_module/`. The reStructuredText files describe the python module files and `sphinx-apidoc` will create them automatically.
5. Genertate the html documentation: `docker run --rm -v  /home/li0nmo0se/project/sphinx_scipy_doc/:/docs mysphinx-latexpdf /bin/sh -c "cd docs && make clean && make html"`
6. **(Linux only)** Change file permission to yourself: `sudo chown -R $(whoami) docs/`. Docker created those files as root and it is not convenient.

## MISC

* In order to change the logo, you may replace `/docs/source/_theme/scipy/static/img/scipy_org_logo.png` by your own logo. Keep the same filename!

## Output generated documentation

![](generated_doc.png)