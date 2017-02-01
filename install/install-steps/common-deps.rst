If not yet installed, install external dependencies:

  - Pip (apt: python-pip)
  - scons (apt: scons)
  - zlib headers (apt: zlib1g-dev)
  - libpng headers (apt: libpng12-dev)
  - PyQt4 (apt: python-qt4)

.. code-block:: bash

  sudo apt-get install python-pip scons zlib1g-dev libpng12-dev python-qt4

Install IPython et Qtconsole:

  - IPython 2.4.1 (apt: ipython)
  - IPython Qtconsole (apt: ipython-qtconsole)

.. warning::

  On ubuntu 16.04, you DONT need to install ipython manually because packaged version is the required one.

.. code-block:: bash

  sudo apt-get install ipython ipython-qtconsole

.. warning::

  On ubuntu 14.04, you need to install ipython manually because packaged version is too old.

.. code-block:: bash

  sudo pip install ipython==2.4.1
  sudo pip install "ipython[qtconsole]"

Install Numpy, Scipy and Matplotlib:

  - Numpy (apt: python-numpy)
  - SciPy (apt: python-scipy)
  - matplotlib (apt: python-matplotlib)

.. code-block:: bash

  sudo apt-get install python-numpy python-scipy python-matplotlib

