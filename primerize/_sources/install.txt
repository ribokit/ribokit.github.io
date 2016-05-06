Installation
------------------

To install ``Primerize``, simply:

.. code-block:: bash
   :linenos:

    cd path/to/primerize/repo
    python setup.py install

For system-wide installation, you must have permissions and use with ``sudo``.

``Primerize`` requires the following *Python* packages as dependencies, all of which can be installed through `pip <https://pip.pypa.io/>`_:

.. code-block:: js
   :linenos:

    llvmlite == 0.8.0
    matplotlib >= 1.5.0
    numba == 0.23.1
    numpy >= 1.10.1
    xlwt >= 1.0.0

* Note that the `numba <http://numba.pydata.org/>`_ is used for its ``@jit`` (`see here <http://numba.pydata.org/numba-doc/0.23.1/user/jit.html>`_) decorator on loop optimization. ``numba`` requires `llvm <http://llvm.org/>`_), which can be installed through `apt-get <https://help.ubuntu.com/lts/serverguide/apt-get.html>`_ on *Linux* or `brew <http://brew.sh/>`_ on Mac *OSX*. It also requires ``llvmlite``, which can be installed through ``pip``. 

* The compatibility between ``numba``, ``llvmlite``, and ``llvm`` needs to pay special attention to. The above specified ``numba`` and ``llvmlite`` versions have been tested to work with ``llvm 3.6.2`` on *Linux* machines. 
