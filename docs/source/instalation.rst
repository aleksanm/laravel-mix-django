Tad kā man gāja
=====

.. _installation:

Sākam
------------

Izveidojam vēlamo folderi. Tajā izveidojam virtual enviroment un aktiviējam:

.. code-block:: console

   $mkdir webpack && cd webpack
   $python -m venv venv
   $source venv/bin/activate
   (venv)$


Vispirms updeitojam pip:

.. code-block:: console
   :dedent: 7

   (venv)$python -m pip install --upgrade pip

Instalējam Django:

.. code-block:: console
   :dedent: 7

   (venv)$pip install django
   
Izveidojam projektu:
  
.. code-block:: console
   :dedent: 7

   (venv)$django-admin startproject webpack
