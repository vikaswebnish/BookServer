**********************
Development guidelines
**********************
This document covers guidelines for developers contributing to this project.

Installation
============

#.  Create a folder to store Runestone-related files. In the following documentation, it's called ``runestone_root``, but any name is fine.
#.  Clone the `Runestone Components repo <https://github.com/RunestoneInteractive/RunestoneComponents>`_ from the ``runestone_root`` directory, then check out the ``bookserver`` branch.
#.  Clone `this <https://github.com/bnmnetp/BookServer>`_ repo from the ``runestone_root`` directory. At this point, your directory structure should look like::

        runestone_root/
            BookServer/
            RunestoneComponents/

#.  `Install poetry <https://python-poetry.org/docs/#installation>`_.
#.  From the command line / terminal, change to the ``runestone_root/BookServer`` then execute ``poetry install``. It will install both the BookServer and the Runestone Components.

Use:

Either prefix all commands with ``poetry run`` (such as ``poetry run bookserver``) or type ``poetry shell`` at a terminal / command prompt to gain access to the BookServer venv. Follow the author directions to install a book, build it, run the server, etc.


Documentation
=============
*   Write documentation using ReStruturedText files instead of Markdown -- RST supports more Sphinx features.
*   Intersphinx is configured, so you can provide hyperlinks directly to Runestone Components. Provide these helps to help illustrate the ways these two codebases interact.
*   Interleave documentation with code based on the `CodeChat style guidelines <https://codechat.readthedocs.io/en/master/docs/style_guide.cpp.html>`_.
*   To add to this program:

    #.  Add comments that describe what you're doing and why.
    #.  Write a function, then write a failing unit test.
    #.  Add comments on your implementation as you write code. Write unit tests as early as possible and test often.
    #.  Add comments after you're finished coding, reflecting on why you chose this particular approach.

*   If you don't understand a part of the code, write documentation for it as you work through the code.


Coding standards
================

.. _pull requests:

Pull requests
-------------
Before submitting code in a pull request, execute `../pre_commit_check.py`. This program will:

*   Verify that `pytest <https://docs.pytest.org/en/stable/>`_ passes. See `../test/toctree` to run the tests.
*   Format your code with `Black <https://github.com/psf/black>`_. From the root directory of the project, run ``black .``.
*   Check that `Flake8 <https://flake8.pycqa.org/en/latest/index.html>`_ finds no problems. See `../.flake8` for directions.
*   `Build the documentation <../conf.py>`, verifying the build produces no errors.

When this passes:

*   Pull from upstream, then `rebase your pull request <https://www.atlassian.com/git/tutorials/merging-vs-rebasing>`_ if necessary to ensure there will be no merge conflicts.
*   Submit your pull request, then verify that CI tests pass.

Rules
^^^^^
#.  No committing to main directly. Mostly a reminder for myself.
#.  In principle I like the idea of rebasing a branch I'm working on locally. But after I publish that branch and make it a PR, no more rebasing after the branch is public.
#.  The main branch should be protected on GitHub so that tests must pass and have an approving review from at least one committer. Ideally this would be someone other than the person who makes the PR but in practice this is hard when people get busy and don't have time to review. Plus I think its fine for self review in small simple cases or emergency bug fixes.
#.  Are a required part of a PR -- we have the opportunity to get our coverage at 100% in these early stages and keep it there as we build out this new server.
#.  I like using semantic versioning, and I've found that doing a weekly release for runestone components works well.  We will strive to follow the same schedule here.

Imports
-------
Use the following template at the top of each Python source file. Use absolute imports instead of relative imports.

.. code:: Python

    # Imports
    # =======
    # These are listed in the order prescribed by `PEP 8`_.
    #
    # Standard library
    # ----------------
    # None. (Or the imports.)
    #
    # Third-party imports
    # -------------------
    # Here's an example...
    from fastapi import FastAPI

    # Local application imports
    # -------------------------
    from BookServer.app import foo