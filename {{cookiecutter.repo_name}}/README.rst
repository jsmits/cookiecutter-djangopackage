=============================
{{ cookiecutter.project_name }}
=============================

.. image:: https://badge.fury.io/py/{{ cookiecutter.repo_name }}.png
    :target: https://badge.fury.io/py/{{ cookiecutter.repo_name }}

.. image:: https://travis-ci.org/{{ cookiecutter.github_username }}/{{ cookiecutter.repo_name }}.png?branch=master
    :target: https://travis-ci.org/{{ cookiecutter.github_username }}/{{ cookiecutter.repo_name }}

{{ cookiecutter.project_short_description}}

Documentation
-------------

The full documentation is at https://{{ cookiecutter.repo_name }}.readthedocs.org.

Quickstart
----------

Install {{ cookiecutter.project_name }}::

    pip install {{ cookiecutter.repo_name }}

Then use it in a project::

    import {{ cookiecutter.app_name }}

Features
--------

* TODO

Development
-----------

Install the test requirements::

    $ pip install -r requirements/dev.txt

Run the tests to check everything is fine::

    $ make test

To run the tests and opening the coverage html in your browser::

    $ make coverage

To run flake8 and pylint, do::

    $ make lint

To generate the documentation, do::

    $ make docs
