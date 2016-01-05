=============
Test projects
=============

Introduction
------------

A unit test is a procedure used to validate that a particular module of
source code is working properly. Unit testing provides a strict and
written contract that the piece of code must satisfy.

This facilitate **refactoring**, by ensuring that the code still
works correctly, and thus encourage developers to improve their code
without the fear to break something.

Unit testing provides a sort of *living document*. Other developers
looking to learn how to use the module can look at the unit tests to
determine how to use the module to fit their needs and gain a basic
understanding of the API.

**A good practice is to write tests before writing source code. Thus tests
becomes a kind of contract that the code must respect.** It is then easy
to check if the implementation respect this contract or not by running the tests.

For each corrected bug, please write a test function. This will ensure
the non regression of the code in later modifications.

Unit test in Python
-------------------

In the OpenAlea framework, Python tests are really important because the
functionalities are accessible via the python interpreter.

Instead of the standard PyUnit python test framework, we highly
recommend to use the
`nose <http://nose.readthedocs.org/en/latest/index.html>`__ framework
for its greater flexibility. A test file is composed with test functions
and classes. They are run in the order in which they appear in the
files.

Tests ensure that the result returned by module function, or behaviour
are correct. Tests are done with the ``assert`` keyword. The test
functions (in a class or not) must begin with ``test_``. Test classes
must begin with ``Test``.

 .. code-block:: python

    # A simple test function
    def test_func():
        x = do_computation()  # must return 2
        assert x == 2

Test functions may define setup and/or teardown attributes, which will
be run before and after the test function, respectively. A convenient
way to do this, especially when several test functions in the same
module need the same setup, is to use the provided ``with_setup``
decorator:

 .. code-block:: python

    def setup_func():
        # ...

    def teardown_func():
        # ...

    @with_setup(setup_func, teardown_func)
    def test():
        # ...

The tests are executed by running *nosetests* in the test directory. All
python files found in the directory are executed. Thus it is possible to
execute all tests at once.

Unit test of data flows
-----------------------

Data flows are python code. However, they require special commands to
execute and test them. Let's suppose you have a dataflow *myflow* into
the package *my.package*. An example of test would be:

 .. code-block:: python

    from openalea.core.alea import run
    from openalea.core.pkgmanager import PackageManager

    # A unique PackageManager is created for all test of dataflow
    pm = PackageManager()
    pm.init(verbose=False)

    def test_myflow():
        """ Test of the data flow myflow """
        res = run(('my.package','myflow'),inputs={},pm=pm)
        assert res == []

This test can then be executed with *nosetests* as previously.

Test generators
---------------

Sometimes, you want to test a bunch of functions or nodes. The first
solution is the brute force where you write a test for each function.
The second method is to build a test generator using nosetests syntax as
follows (example from nose documentation).

 .. code-block:: python

    def test_evens():
        for i in range(0, 5):
             yield check_even, i, i*3

    def check_even(n, nn):
        # your code here

This will result in four tests. nose will iterate the generator,
creating a function test case wrapper for each tuple it yields.

Unit test in C++
----------------

There are several `C++ unit test
framework <http://www.gamesfromwithin.com/articles/0412/000061.html>`__
available out there. No framework have been choose at this time. Wait
and stay tuned.

Nosetests usage with setuptools
-------------------------------

In order to launch the tests go in your package directory (where you can
found the file *setup.py*). In principle, there is a test directory. Type::

    python setup.py nosetests -w test

This command will run all the files that contain the word ``test`` that
are found in the directory *test*.

If you want to run nosetests on a particular test (let us call
*test_nose.py*) then type::

    python setup.py nosetests -w test --tests test_nose

(extension is not required)

Note that you can add the option -v (in the commands above) to get more
verbose information
