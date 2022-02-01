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
   
   (venv)$ python -m pip install --upgrade pip

Instalējam Django:

.. code-block:: console
   
   (venv)$ pip install django
   
Izveidojam projektu:
  
.. code-block:: console
   
   (venv)$ django-admin startproject mysite .
   
Atceramies par "." beigās

Ruļījam tālāk:
izveidojam konfigurācijas failu priekš laravel-mix:

.. code-block:: console
   
   $ touch webpack.mix.js

Inicializējam npm:

.. code-block:: console

   $ npm init -y

Instalējam laravel-mix:

.. code-block:: console

   $ npm install laravel-mix

.. code-block:: console
   $ 
