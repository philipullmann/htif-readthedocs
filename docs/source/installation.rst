Installation
=============================

Dependencies
------------

HTIF C++ is built upon the following packages:

- RDKit 2024.09.3+ (`Reference <https://www.rdkit.org/docs/Install.html>`__)

By default, conda will install all the dependencies.

Installation
------------

We will set up the environment using `Anaconda <https://docs.anaconda.com/anaconda/install/index.html>`_.


.. code-block:: console

   $ git clone https://github.com/philipullmann/HTIF.git
    

Mac OS and Linux
^^^^^^^^^^^^^^^^^^^^^^^^^^^

For UNIX-based systems (Mac OS and Linux), the installation and building process could be done quite straightforwardly. In the same folder as previous steps, use:

.. code-block:: console
   
   $ conda env create -f HTIF/environment.yml
   $ conda activate htif
   $ pip install -e htif


Windows:
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Will be added later



Testing:
------------

Will be added later