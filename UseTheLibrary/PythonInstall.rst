Install Python bindings
~~~~~~~~~~~~~~~~~~~~~~~

Windows
-------

Install the bindings
^^^^^^^^^^^^^^^^^^^^

#. First you need to download and install the main Open Babel executable
   and library as described in :ref:`Install binaries`.
#. Next, use ``pip`` to install the Python bindings::

    pip install -U openbabel

**Note**: Python is available as either a 32-bit or 64-bit version. You need to install the corresponding version of Open Babel in step 1.

Install Pillow (optional)
^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to display 2D depictions using Pybel (rather than just write to 
a file), you need to install the Pillow library::

   pip install -U pillow

Test the installation
^^^^^^^^^^^^^^^^^^^^^

Open a Windows command prompt, and type the following commands to
make sure that everything is installed okay. If you get an error
message, there's something wrong and you should email the mailing
list with the output from these commands.

::

    C:\Documents and Settings\Noel> obabel -V
    Open Babel 3.0.0 -- Oct  7 2019 -- 20:18:16
    
    C:\Documents and Settings\Noel> obabel -Hsdf
    sdf  MDL MOL format
    Reads and writes V2000 and V3000 versions

    Read Options, e.g. -as
     s  determine chirality from atom parity flags
    ...
    ...
    
    C:\Documents and Settings\Noel> dir "%BABEL_DATADIR%"\mr.txt
     Volume in drive C has no label.
     Volume Serial Number is 68A3-3CC9
    
     Directory of C:\Users\Noel\AppData\Roaming\OpenBabel-3.0.0\data

    06/10/2019  16:37             4,295 mr.txt
                   1 File(s)          4,295 bytes
                   0 Dir(s)  58,607,575,040 bytes free
    
    C:\Documents and Settings\Noel> py
    Python 2.7.16 (v2.7.16:413a49145e, Mar  4 2019, 01:37:19) [MSC v.1500 64
    bit (AMD64)] on win32
    Type "help", "copyright", "credits" or "license" for more information.
    >>> from openbabel import pybel
    >>> mol = pybel.readstring("smi", "CC(=O)Br")
    >>> mol.make3D()
    >>> print(mol.write("sdf"))
    
     OpenBabel01010918183D
    
      7  6  0  0  0  0  0  0  0  0999 V2000
        1.0166   -0.0354   -0.0062 C   0  0  0  0  0
        2.5200   -0.1269    0.0003 C   0  0  0  0  0
        3.0871   -1.2168    0.0026 O   0  0  0  0  0
        3.2979    1.4258    0.0015 Br  0  0  0  0  0
        0.6684    1.0007    0.0052 H   0  0  0  0  0
        0.6255   -0.5416    0.8803 H   0  0  0  0  0
        0.6345   -0.5199   -0.9086 H   0  0  0  0  0
      1  2  1  0  0  0
      1  5  1  0  0  0
      1  6  1  0  0  0
      1  7  1  0  0  0
      2  4  1  0  0  0
      2  3  2  0  0  0
    M  END
    $$$$
    >>> mol.draw() # If you installed PIL, this will display its structure
    >>> (Hit CTRL+Z followed by Enter to exit)

Linux and MacOSX
----------------

See :ref:`Compile bindings` for information on how to configure CMake to compile the Python bindings. This can be done either globally or locally.

You may need to add the location of :file:`libopenbabel.so` (on my system, the location is :file:`/usr/local/lib`) to the environment variable LD\_LIBRARY\_PATH if you get the following error when you try to import the OpenBabel library at the Python prompt:

::

    $ python
    >>> from openbabel import openbabel 
    Traceback (most recent call last):
      File "<stdin>", line 1, in
      File "/usr/lib/python2.4/site-packages/openbabel.py", line 9, in
       import _openbabel
    ImportError: libopenbabel.so.3: cannot open shared object file: No such file or directory

Install Pillow (optional)
^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to display 2D depictions using Pybel (rather than just write to
a file), you need the Pillow library, and the Python Tkinter library (part of the standard library).
These should be available through
your package manager, e.g. on Ubuntu, Pillow is provided by 'python-pil' and
'python-pil.imagetk', while Tkinter is provided by 'python-tk'.
