Tad kā man gāja
=====

.. _installation:

Sākam
------------

Izveidojam vēlamo folderi. Tajā izveidojam virtual enviroment un aktiviējam:

.. code-block:: bash

   $mkdir webpack && cd webpack
   $python -m venv venv
   $source venv/bin/activate
   (venv)$

Vispirms updeitojam pip:

.. code-block:: bash
   
   $VENV python -m pip install --upgrade pip

Instalējam Django:

.. code-block:: bash
   
   $VENV pip install django
   
Izveidojam projektu:
  
.. code-block:: bash
   
   $VENV django-admin startproject webpack

