=======================
Project's documentation
=======================

General guidelines
------------------

A general guide to documenting python code can be found on
`python.org <https://docs.python.org/devguide/documenting.html>`_.


`Sphinx <http://sphinx-doc.org/index.html>`_ is used to render docstrings into
html developer manual. A simple intro to *Sphinx* can be found on it's
`website <https://pythonhosted.org/an_example_pypi_project/sphinx.html>`_.

Documentation Style
-------------------

Follow `PEP257 <https://www.python.org/dev/peps/pep-0257/>`__ for docstring
conventions and use Google doc style. An example can be found on
`napoleon <http://sphinxcontrib-napoleon.readthedocs.org/en/latest/example_google.html#example-google>`_

Type specification
------------------

Use the following convention to specify the expected type of a parameter in your
docstrings:

Simple Types
^^^^^^^^^^^^

  int, float, None, str, bool, cplx, slice

Any Type
^^^^^^^^

  any

Classes
^^^^^^^

  class
  subclass of classname

Complex Types
^^^^^^^^^^^^^

  class
  module.class

Containers
^^^^^^^^^^

  - tuple [ of value ]
  - list [ of value ]
  - dict [ of key:value ]
  - iter [ of value ]
  - '(v1, v2, v3, ...)' ou 'v1, v2, v3, ...' for return values
  - other [ of value ]

Functions
^^^^^^^^^

  func(arg1, arg2, ...) -> return

Examples
^^^^^^^^

  - list of int|float = list of integer or float
  - list of (int,int) = list of tuple (int,int)
  - list of any = list of any type of element
  - iter of func(int,int)->float
  - dict of str:any = map of string -> any type of element
