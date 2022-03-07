# Sphinx scipy documentation sphinx

## Step by step


Copy `docs` folder in the root directory

docker build -t mysphinx-latexpdf -f docs/Dockerfile .
docker run --rm -v /home/li0nmo0se/project/sphinx_scipy_doc/:/docs mysphinx-latexpdf sphinx-apidoc -f -o ./docs/source  my_module/
docker run --rm -v  /home/li0nmo0se/project/sphinx_scipy_doc/:/docs mysphinx-latexpdf /bin/sh -c "cd docs && make clean && make html"
sudo chown -R li0nmo0se docs/

## MISC

* In order to change the logo, you may replace `/docs/source/_theme/scipy/static/img/scipy_org_logo.png` by your own logo. Keep the same filename!