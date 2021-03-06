==========================
robotframework-unixfilesystem
==========================

**robotframework-unixfilesystem** is a `Robot Framework
<http://code.google.com/p/robotframework/>`_ test library to test
UNIX filesystem attributes like permissions, ownership etc.

Installation
++++++++++++

To install, just fetch the latest version from PyPI:.

    pip install --upgrade robotframework-unixfilesystem

Usage
+++++

Setup in the robotframework Settings section:

============  ================
  Setting          Value
============  ================
Library          UnixFilesystemLibrary
============  ================

\

These keyword actions are available::

    Get Owner From Path:
        Does an lstat on the Path and returns the owner of the file/directory:

        Arguments:
            - path:      the path to the file/directory you wish to get ownership
                         on (e.g. /tmp/test.txt or ../foo)
        Return:
            - owner:     returns the owner of the file (e.g. root or chris)

    Owner From Path Should Match:
        Does an lstat on the Path and checks to see if the supplied owner matches.

        Fails test if owner is not matching

        Arguments:
            - owner:     the username to check against ownership of the path
                         (e.g. root or chris)
            - path:      the path to the file/directory you wish to get ownership
                         on (e.g. /tmp/test.txt or ../foo)


    Get Group From Path:
        Does an lstat on the Path and returns the group of the file/directory:

        Arguments:
            - path:      the path to the file/directory you wish to get group
                         membership on (e.g. /tmp/test.txt or ../foo)
        Return:
            - group:     returns the group of the file (e.g. root or chris)

    Group From Path Should Match:
        Does an lstat on the Path and checks to see if the supplied group matches.

        Fails test if group is not matching

        Arguments:
            - group:     the username to check against groupship of the path
                         (e.g. root or chris)
            - path:      the path to the file/directory you wish to get groupship
                         on (e.g. /tmp/test.txt or ../foo)


    Get Permissions From Path As Octal
        Gets the permissions via lstat of the supplied Path and returns those permissions as
        an octal value.

        Arguments:
            - path:      the path to the file/directory you wish to get ownership on
                         (e.g. /tmp/test.txt or ../foo)
        Return:
            - permissions: Returns the octal permissions of the path (e.g. 0755 or 0644)

    Permissions From Path Should Match:
        Gets the permissions via lstat of the supplied Path and checks if those permissions
        match the supplied Permissions.

        Fails test if persmissions is not matching

        Arguments:
            - path:      the path to the file/directory you wish to get ownership on
                         (e.g. /tmp/test.txt or ../foo)
            - permissions: octal permissions (e.g. 0755 or 0644)



Here is an example of how to use the library:

==================  ==========================  ===================================
 Action             Argument                    Argument
==================  ==========================  ===================================
${Owner}=           Get Owner From Path         path=/tmp/test.txt
Should Match        ${Owner}                    root
==================  ==========================  ===================================

Here is an example of how to check that the owner of a path matches the supplied owner

============================ ==========================  ===================================
 Action                      Argument                    Argument
============================ ==========================  ===================================
Owner From Path Should Match root                        path=/tmp/text.txt
============================ ==========================  ===================================

Here is an example of how to get permissions from the path as an octal

================== ================================== ===================================
 Action            Argument                           Argument
================== ================================== ===================================
${Permissions}     Get Permissions From Path as Octal path=/tmp/
Should Match       ${Permissions}                     0644
================== ================================== ===================================

Here is an example of how to check that permissions from the path match the octal

================================== ==========================
 Action                            Argument
================================== ==========================
Permissions From Path Should Match 0644
================================== ==========================

Updating Pip Repo
+++++++

    python setup.py sdist

    twine upload dist/*


License
+++++++

The robotframework-unixfilesystem is licensed under the `Apache 2.0 License
<http://www.apache.org/licenses/LICENSE-2.0.html>`_.
