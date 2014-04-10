.. _install-osx:

Installing Python on Mac OS X
=============================

The latest version of Mac OS X, Mavericks, **comes with Python 2.7 out of the box**.

You do not need to install or configure anything else to use Python. Having
said that, I would strongly recommend that you install the tools and libraries
described in the next section before you start building Python applications
for real-world use. In particular, you should always install Setuptools, as it
makes it much easier for you to use other third-party Python libraries.

The version of Python that ships with OS X is great for learning. Yet, it's not
good for development. The version shipped with OS X may be out of date from the
`official current Python release <https://www.python.org/downloads/mac-osx/>`_,
which is considered the stable production version.

Doing it Right
--------------

Let's install a real version of Python.

Before installing Python, you'll need to install GCC. GCC can be obtained
by downloading `XCode <http://developer.apple.com/xcode/>`_, the smaller
`Command Line Tools <https://developer.apple.com/downloads/>`_ (must have an
Apple account) or the even smaller `OSX-GCC-Installer <https://github.com/kennethreitz/osx-gcc-installer#readme>`_
package.

.. note::
    If you already have XCode installed, do not install OSX-GCC-Installer.
    In combination, the software can cause issues that are difficult to
    diagnose.

While OS X comes with a large number of UNIX utilities, those familiar with
Linux systems will notice one key component missing: a decent package manager.
`Homebrew <http://brew.sh>`_ fills this void.

To `install Homebrew <https://github.com/Homebrew/homebrew/wiki/installation>`_,
simply run

.. code-block:: console

    $ ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)" 

The script will explain what changes it will make and prompt you before the
installation begins.
Once you've installed Homebrew, insert the Homebrew directory at the top
of your :envvar:`PATH` environment variable. You can do this by adding the following
line at the bottom of your :file:`~/.bashrc` file

.. code-block:: console

    export PATH=/usr/local/bin:/usr/local/sbin:$PATH

Now, we can install Python 2.7:

.. code-block:: console

    $ brew install python

This will take a minute or two. Once that's complete, you'll have to add the
new Python scripts directory to your :envvar:`PATH`:

.. code-block:: console

    export PATH=/usr/local/share/python:$PATH


Setuptools & Pip
----------------

The most crucial third-party Python software of all is Setuptools, which
extends the packaging and installation facilities provided by the distutils
in the standard library. Once you add Setuptools to your Python system you can
download and install any compliant Python software product with a single
command. It also enables you to add this network installation capability to
your own Python software with very little work. Homebrew already installed
Setuptools for you.

Happily, when you ran ``brew install python``, Homebrew also installed :program:`pip`.
Pip allows for installation and uninstallation of packages, and is actively
maintained.


Virtualenv
----------

After Setuptools and Pip, the next development tool that you should install is
`virtualenv <http://pypi.python.org/pypi/virtualenv/>`_. Use pip

.. code-block:: console

    $ pip install virtualenv

The :program:`virtualenv` kit provides the ability to create virtual Python environments
that do not interfere with either each other, or the main Python installation.
If you install :program:`virtualenv` before you begin coding then you can get into the
habit of using it to create completely clean Python environments for each
project. This is particularly important for Web development, where each
framework and application will have many dependencies.

To set up a new Python environment, move into the directory where you would 
like to store the environment, and use the :program:`virtualenv` utility to create 
the new environment.

.. code-block:: console

    $ virtualenv venv

To use an environment, run ``source venv/bin/activate``. Your command prompt
will change to show the active environment. Once you have finished working in
the current virtual environment, run ``deactivate`` to restore your settings
to normal.

Each new environment automatically includes a copy of :program:`pip`, so that you can
setup the third-party libraries and tools that you want to use in that
environment. Put your own code within a subdirectory of the environment,
however you wish. When you no longer need a particular environment, simply
copy your code out of it, and then delete the main directory for the environment.

An useful set of extensions to :program:`virtualenv` is available in 
:program:`virtualenvwrapper`. `RTFD <http://virtualenvwrapper.readthedocs.org/en/latest/>`_ to find out more.

--------------------------------

This page is a remixed version of `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
which is available under the same license.
