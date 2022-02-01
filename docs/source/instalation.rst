Tad kā man gāja
=====

.. _installation:

Sākam..
------------

Izveidojam vēlamo folderi. Tajā izveidojam virtual enviroment un kativiējam:

.. code-block:: console

   $ mkdir webpack && cd webpack
   $ python -m venv venv
   $source venv/bin/activate


Vispirms updeitojam pip:

.. code-block:: console

   (.venv) $ python -m pip install --upgrade pip

Izveidojam vēlamo folderi un uzinstalējam Django:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

