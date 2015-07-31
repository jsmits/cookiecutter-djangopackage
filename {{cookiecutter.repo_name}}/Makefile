.PHONY: clean-pyc clean-build docs

help:
	@echo "clean-build - remove build artifacts"
	@echo "clean-pyc - remove python file artifacts"
	@echo "clean - run clean-build and clean-pyc"
	@echo "lint - check style with flake8 and pylint"
	@echo "test - run tests quickly with the default python"
	@echo "test-all - run tests on every python version with tox"
	@echo "coverage - check code coverage quickly with the default python"
	@echo "docs - generate Sphinx HTML documentation, including API docs"
	@echo "release - make a release with zest.releaser's fullrelease"

clean: clean-build clean-pyc

clean-build:
	rm -fr build/
	rm -fr dist/
	rm -fr *.egg-info

clean-pyc:
	find . -name '*.pyc' -exec rm -f {} +
	find . -name '*.pyo' -exec rm -f {} +
	find . -name '*~' -exec rm -f {} +

lint:
	flake8 {{ cookiecutter.app_name }} tests --exit-zero
	pylint --load-plugins pylint_django -f colorized --rcfile=.pylint.cfg --disable=I0011 -j 4 -r n {{ cookiecutter.app_name }}/ tests/

test:
	coverage run --source {{ cookiecutter.app_name }} -m py.test -v
	coverage report -m

test-all:
	tox

coverage: test
	coverage html
	open htmlcov/index.html

docs:
	export DJANGO_SETTINGS_MODULE=tests.settings
	rm -f docs/{{ cookiecutter.repo_name }}.rst
	rm -f docs/modules.rst
	sphinx-apidoc -o docs/ {{ cookiecutter.app_name }}
	$(MAKE) -C docs clean
	$(MAKE) -C docs html
	open docs/_build/html/index.html

release:
	prerelease
	rm -f docs/{{ cookiecutter.repo_name }}.rst
	rm -f docs/modules.rst
	sphinx-apidoc -o docs/ {{ cookiecutter.app_name }}
	$(MAKE) -C docs clean
	$(MAKE) -C docs html
	postrelease
