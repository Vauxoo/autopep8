========
autopep8
========

.. image:: https://travis-ci.org/hhatto/autopep8.svg?branch=master
    :target: https://travis-ci.org/hhatto/autopep8
    :alt: Build status

autopep8 automatically formats Python code to conform to the `PEP 8`_ style
guide. It uses the pep8_ utility to determine what parts of the code needs to
be formatted. autopep8 is capable of fixing most of the formatting issues_ that
can be reported by pep8.

.. _PEP 8: http://www.python.org/dev/peps/pep-0008/
.. _issues: https://pep8.readthedocs.org/en/latest/intro.html#error-codes

.. contents::


Installation
============

From pip::

    $ pip install --upgrade autopep8

Consider using the ``--user`` option_.

.. _option: https://pip.readthedocs.org/en/latest/user_guide.html#user-installs


Requirements
============

autopep8 requires pep8_.

.. _pep8: https://github.com/PyCQA/pep8


Usage
=====

To modify a file in place (with aggressive level 2)::

    $ autopep8 --in-place --aggressive --aggressive <filename>

Before running autopep8.

.. code-block:: python

    import math, sys;

    def example1():
        ####This is a long comment. This should be wrapped to fit within 72 characters.
        some_tuple=(   1,2, 3,'a'  );
        some_variable={'long':'Long code lines should be wrapped within 79 characters.',
        'other':[math.pi, 100,200,300,9876543210,'This is a long string that goes on'],
        'more':{'inner':'This whole logical line should be wrapped.',some_tuple:[1,
        20,300,40000,500000000,60000000000000000]}}
        return (some_tuple, some_variable)
    def example2(): return {'has_key() is deprecated':True}.has_key({'f':2}.has_key(''));
    class Example3(   object ):
        def __init__    ( self, bar ):
         #Comments should have a space after the hash.
         if bar : bar+=1;  bar=bar* bar   ; return bar
         else:
                        some_string = """
    		           Indentation in multiline strings should not be touched.
    Only actual code should be reindented.
    """
                        return (sys.path, some_string)

After running autopep8.

.. code-block:: python

    import math
    import sys


    def example1():
        # This is a long comment. This should be wrapped to fit within 72
        # characters.
        some_tuple = (1, 2, 3, 'a')
        some_variable = {
            'long': 'Long code lines should be wrapped within 79 characters.',
            'other': [
                math.pi,
                100,
                200,
                300,
                9876543210,
                'This is a long string that goes on'],
            'more': {
                'inner': 'This whole logical line should be wrapped.',
                some_tuple: [
                    1,
                    20,
                    300,
                    40000,
                    500000000,
                    60000000000000000]}}
        return (some_tuple, some_variable)


    def example2():
        return ('' in {'f': 2}) in {'has_key() is deprecated': True}


    class Example3(object):

        def __init__(self, bar):
            # Comments should have a space after the hash.
            if bar:
                bar += 1
                bar = bar * bar
                return bar
            else:
                some_string = """
    		           Indentation in multiline strings should not be touched.
    Only actual code should be reindented.
    """
                return (sys.path, some_string)

Options::

    usage: autopep8 [-h] [--version] [-v] [-d] [-i] [--global-config filename]
                    [--ignore-local-config] [-r] [-j n] [-p n] [-a]
                    [--experimental] [--exclude globs] [--list-fixes]
                    [--ignore errors] [--select errors] [--max-line-length n]
                    [--line-range line line] [--indent-size n]
                    [files [files ...]]

    Automatically formats Python code to conform to the PEP 8 style guide.

    positional arguments:
      files                 files to format or '-' for standard in

    optional arguments:
      -h, --help            show this help message and exit
      --version             show program's version number and exit
      -v, --verbose         print verbose messages; multiple -v result in more
                            verbose messages
      -d, --diff            print the diff for the fixed source
      -i, --in-place        make changes to files in place
      --global-config filename
                            path to a global pep8 config file; if this file does
                            not exist then this is ignored (default:
                            ~/.config/pep8)
      --ignore-local-config
                            don't look for and apply local config files; if not
                            passed, defaults are updated with any config files in
                            the project's root directory
      -r, --recursive       run recursively over directories; must be used with
                            --in-place or --diff
      -j n, --jobs n        number of parallel jobs; match CPU count if value is
                            less than 1
      -p n, --pep8-passes n
                            maximum number of additional pep8 passes (default:
                            infinite)
      -a, --aggressive      enable non-whitespace changes; multiple -a result in
                            more aggressive changes
      --experimental        enable experimental fixes
      --exclude globs       exclude file/directory names that match these comma-
                            separated globs
      --list-fixes          list codes for fixes; used by --ignore and --select
      --ignore errors       do not fix these errors/warnings (default: E24)
      --select errors       fix only these errors/warnings (e.g. E4,W)
      --max-line-length n   set maximum allowed line length (default: 79)
      --line-range line line, --range line line
                            only fix errors found within this inclusive range of
                            line numbers (e.g. 1 99); line numbers are indexed at
                            1
      --indent-size n       number of spaces per indent level (default 4)


Features
========

autopep8 fixes the following issues_ reported by pep8_::

    E101 - Reindent all lines.
    E121 - Fix indentation to be a multiple of four.
    E122 - Add absent indentation for hanging indentation.
    E123 - Align closing bracket to match opening bracket.
    E124 - Align closing bracket to match visual indentation.
    E125 - Indent to distinguish line from next logical line.
    E126 - Fix over-indented hanging indentation.
    E127 - Fix visual indentation.
    E128 - Fix visual indentation.
    E20  - Remove extraneous whitespace.
    E211 - Remove extraneous whitespace.
    E22  - Fix extraneous whitespace around keywords.
    E224 - Remove extraneous whitespace around operator.
    E226 - Fix missing whitespace around arithmetic operator.
    E227 - Fix missing whitespace around bitwise/shift operator.
    E228 - Fix missing whitespace around modulo operator.
    E231 - Add missing whitespace.
    E241 - Fix extraneous whitespace around keywords.
    E242 - Remove extraneous whitespace around operator.
    E251 - Remove whitespace around parameter '=' sign.
    E26  - Fix spacing after comment hash for inline comments.
    E265 - Fix spacing after comment hash for block comments.
    E27  - Fix extraneous whitespace around keywords.
    E301 - Add missing blank line.
    E302 - Add missing 2 blank lines.
    E303 - Remove extra blank lines.
    E304 - Remove blank line following function decorator.
    E309 - Add missing blank line (after class declaration).
    E401 - Put imports on separate lines.
    E501 - Try to make lines fit within --max-line-length characters.
    E502 - Remove extraneous escape of newline.
    E701 - Put colon-separated compound statement on separate lines.
    E70  - Put semicolon-separated compound statement on separate lines.
    E711 - Fix comparison with None.
    E712 - Fix comparison with boolean.
    E721 - Use "isinstance()" instead of comparing types directly.
    W291 - Remove trailing whitespace.
    W293 - Remove trailing whitespace on blank line.
    W391 - Remove trailing blank lines.
    W601 - Use "in" rather than "has_key()".
    W602 - Fix deprecated form of raising exception.
    W603 - Use "!=" instead of "<>"
    W604 - Use "repr()" instead of backticks.
    W690 - Fix various deprecated code (via lib2to3).

autopep8 also fixes some issues not found by pep8_.

- Correct deprecated or non-idiomatic Python code (via ``lib2to3``). Use this
  for making Python 2.6 and 2.7 code more compatible with Python 3. (This is
  triggered if ``W690`` is enabled.)
- Normalize files with mixed line endings.
- Put a blank line between a class declaration and its first method
  declaration. (Enabled with ``E309``.)
- Put a blank line between a class docstring and its first method
  declaration. (Enabled with ``E301``.)
- Remove blank lines between a function declaration and its docstring. (Enabled
  with ``E303``.)

autopep8 avoids fixing some issues found by pep8_.

- ``E112``/``E113`` for non comments are reports of bad indentation that break
  syntax rules. These should not be modified at all.
- ``E265``, which refers to spacing after comment hash, is ignored if the
  comment looks like code. autopep8 avoids modifying these since they are not
  real comments. If you really want to get rid of the pep8_ warning, consider
  just removing the commented-out code. (This can be automated via eradicate_.)

.. _eradicate: https://github.com/myint/eradicate


More advanced usage
===================

By default autopep8 only makes whitespace changes. Thus, by default, it does
not fix ``E711`` and ``E712``. (Changing ``x == None`` to ``x is None`` may
change the meaning of the program if ``x`` has its ``__eq__`` method
overridden.) Nor does it correct deprecated code ``W6``. To enable these
more aggressive fixes, use the ``--aggressive`` option::

    $ autopep8 --aggressive <filename>

Use multiple ``--aggressive`` to increase the aggressiveness level. For
example, ``E712`` requires aggressiveness level 2 (since ``x == True`` could be
changed to either ``x`` or ``x is True``, but autopep8 chooses the former).

``--aggressive`` will also shorten lines more aggressively. It will also remove
trailing whitespace more aggressively. (Usually, we don't touch trailing
whitespace in docstrings and other multiline strings. And to do even more
aggressive changes to docstrings, use docformatter_.)

.. _docformatter: https://github.com/myint/docformatter

To enable only a subset of the fixes, use the ``--select`` option. For example,
to fix various types of indentation issues::

    $ autopep8 --select=E1,W1 <filename>

Similarly, to just fix deprecated code::

    $ autopep8 --aggressive --select=W6 <filename>

The above is useful when trying to port a single code base to work with both
Python 2 and Python 3 at the same time.

If the file being fixed is large, you may want to enable verbose progress
messages::

    $ autopep8 -v <filename>


Use as a module
===============

The simplest way of using autopep8 as a module is via the ``fix_code()``
function:

    >>> import autopep8
    >>> autopep8.fix_code('x=       123\n')
    'x = 123\n'

Or with options:

    >>> import autopep8
    >>> autopep8.fix_code('x.has_key(y)\n',
    ...                   options={'aggressive': 1})
    'y in x\n'
    >>> autopep8.fix_code('print( 123 )\n',
    ...                   options={'ignore': ['E']})
    'print( 123 )\n'


Testing
=======

Test cases are in ``test/test_autopep8.py``. They can be run directly via
``python test/test_autopep8.py`` or via tox_. The latter is useful for
testing against multiple Python interpreters. (We currently test against
CPython versions 2.6, 2.7, 3.2, and 3.3. We also test against PyPy.)

.. _`tox`: https://pypi.python.org/pypi/tox

Broad spectrum testing is available via ``test/acid.py``. This script runs
autopep8 against Python code and checks for correctness and completeness of the
code fixes. It can check that the bytecode remains identical.
``test/acid_pypi.py`` makes use of ``acid.py`` to test against the latest
released packages on PyPI.


Troubleshooting
===============

``pkg_resources.DistributionNotFound``
--------------------------------------

If you are using an ancient version of ``setuptools``, you might encounter
``pkg_resources.DistributionNotFound`` when trying to run ``autopep8``. Try
upgrading ``setuptools`` to workaround this ``setuptools`` problem::

    $ pip install --upgrade setuptools

Use ``sudo`` if you are installing to the system.


Links
=====

* PyPI_
* GitHub_
* `Travis CI`_
* Coveralls_
* Jenkins_

.. _PyPI: https://pypi.python.org/pypi/autopep8/
.. _GitHub: https://github.com/hhatto/autopep8
.. _`Travis CI`: https://travis-ci.org/hhatto/autopep8
.. _`Coveralls`: https://coveralls.io/r/hhatto/autopep8
.. _Jenkins: http://jenkins.hexacosa.net/job/autopep8/
