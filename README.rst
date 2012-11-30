Introduction
============

``bobtemplates.kotti`` provides `mr.bob`_ templates to generate packages for
the `Kotti CMS`_

Available templates are:

    -   ``theme``: a simple template for a Kotti theme package

Global settings
---------------

Some variables are used with every template.  These should be added to the
mr.bob user config in ``~/.mrbob``, e.g.::

    [variables]

    author.name = Andreas Kaiser
    author.email = disko@binary-punks.com
    author.github.user = disko

Creating a theme package
------------------------

To create a Kotti theme run::

    mrbob -O kotti_theme_spacelab bobtemplates.kotti:theme

and answer the questions::

    Welcome to mr.bob interactive mode. Before we generate directory structure,
    some questions need to be answered.

    Answer with a question mark to display help.
    Value in square brackets at the end of the questions present default value
    if there is no answer.


    --> Name of the package: kotti_theme_spacelab

    --> Version of the package [0.1]:

    --> License of the package [BSD]:

    --> Name of the theme: Spacelab

    --> Original URL of the wrapped theme: http://bootswatch.com/spacelab/

Add a Bootstrap CSS file::

    cd kotti_theme_spacelab/kotti_theme_spacelab/static/css/
    wget http://bootswatch.com/spacelab/bootstrap.css

Setup the package and run the CSS/JS minifier::

    cd ../../../
    python setup.py develop
    python setup.py dev
    python setup.py minify

Run the demo::

    pserve development.ini

Point your browser to ``http://127.0.0.1:5000`` and enjoy your themed Kotti
site.

.. _mr.bob: http://mrbob.readthedocs.org/en/latest/
.. _Kotti CMS: http://kotti.readthedocs.org/en/latest/
