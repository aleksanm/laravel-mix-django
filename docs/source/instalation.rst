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

Ruļījam tālāk un izveidojam konfigurācijas failu priekš laravel-mix:

.. code-block:: console
   
   $ touch webpack.mix.js

Inicializējam npm:

.. code-block:: console

   $ npm init -y

Instalējam laravel-mix:

.. code-block:: console

   $ npm install laravel-mix

Tad uztaisam direktoriju assets ar apakšdirektorijām un failiem

Jābūt šādi:

.. code-block:: console
   
   webpack
      ├── HOWTO.rst
      ├── assets
      │   ├── css
      │   ├── js
      │   └── scss
      ├── manage.py
      ├── mysite
      │   ├── __init__.py
      │   ├── asgi.py
      │   ├── settings.py
      │   ├── urls.py
      │   └── wsgi.py
      ├── node_modules [507 entries exceeds filelimit, not opening dir]
      ├── package-lock.json
      ├── package.json
      ├── venv
      │   ├── bin
      │   ├── include
      │   ├── lib
      │   ├── lib64 -> lib
      │   ├── pyvenv.cfg
      │   └── share
      └── webpack.mix.js
      
   
