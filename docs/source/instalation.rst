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

Tad uztaisam direktoriju assets ar apakšdirektorijām un failiem (css,js,scss) un tajos attiecīgi app.css, app.js/bootstrap.js, app.scss

Pieliekam vēl klāt direktoriju static ar apakšdirektorijām css un js:

Jābūt šādi:

.. code-block:: console

   webpack
      ├── HOWTO.rst
      ├── assets
      │   ├── css
      │   │   └── app.css
      │   ├── js
      │   │   ├── app.js
      │   │   └── bootstrap.js
      │   └── scss
      │       └── app.scss
      ├── manage.py
      ├── mix-manifest.json
      ├── mysite
      │   ├── __init__.py
      │   ├── asgi.py
      │   ├── settings.py
      │   ├── urls.py
      │   └── wsgi.py
      ├── node_modules
      ├── package-lock.json
      ├── package.json
      ├── static
      │   └── mysite
      │       ├── css
      │       └── js
      ├── venv
      └── webpack.mix.js


Rediģējam webpack.mix.js:

.. code-block:: console

   // webpack.mix.js

   let mix = require('laravel-mix');

   mix.js('assets/js/app.js', 'static/mysite/js')
      .sass('assets/scss/app.scss', 'static/mysite/css/')
      .css('assets/css/app.css', 'static/mysite/css');


Instalējam jquery ar npm:

.. code-block:: console

   npm install jquery

Rediģējam webpack.mix.js un pievienojam jquery, lai ņem src nevis dist:

.. code-block:: console

   ...
   
   mix.webpackConfig({
      resolve: {
         alias: {
               jquery: 'jquery/src/jquery'
         }
      }
   });

   ...

Rediģējam assets/js/bootstrap.js un pievienojam instalēto jquery:

.. code-block:: console

   import $ from 'jquery';
   window.$ = window.jQuery = $;

Rediģējam assets/js/app.js un importējam augstākminēto bootstrap.js failu:

.. code-block:: console

   import './bootstrap';

Palaižam komandu:

.. code-block:: console

   npx mix 

Tā pieinstalē trūkstošās pakas un palaižam vēlreiz:

.. code-block:: console

   npx mix

   rezultāts: ✔ Compiled Successfully in 827ms


Redzam, ka ir parādījies fails app.js direktorijā static/js/app.js un ir aizpildījies ar saturu

Redzam, ka ir parādījies fails app.css direktorijā static/css/app.css un ir aizpildījies ar saturu (šobrīd nav stilu, nav satura)

Tad instalējam bootstrap 5 un popperjs:

.. code-block:: console

   npm install bootstrap

   npm install @popperjs/core

Pievienojam failā assets/scss/app.scss bootstrap ierakstu:

.. code-block:: console

   @import "~bootstrap/scss/bootstrap";

Rediģējam assets/js/app.js un importējam bootstrap un lodash:

.. code-block:: console

   ...

   window._ = require("lodash");
   import "bootstrap";

Notestējam ar npx mix ✔ Compiled Successfully in 4392ms

Redzam, ka ir aizpildījies static/css/app.css fails ar saturu

Tas viss. 

apache2 lai servē izveidotos failus, kurus tur iemovos collectstatic komanda

Dgango settings.py norādam root static directoriju un arī STATIC_ROOT absolute path

manā gadījumā:

.. code-block:: console

   ...

   STATICFILES_DIRS = [
      BASE_DIR / "static",
   ]

   STATIC_ROOT= '/var/www/html/static'

   ...

Tagad django palaižam statiskos kolekcionētājus no direktorijas, kur ir manage.py:

.. code-block:: console

   cd ..

   python3 manage.py collectstatic

Un norādītajā direktorijā ir ievācies static saturs!!!

Tad visos html failos head sadaļā:

.. code-block:: console

   ...

   {% load static %}
      <link rel="stylesheet" type="text/css" href="{% static 'mysite/css/app.css' %}">
      <script src="{% static 'mysite/js/app.js' %}"></script>

   ...

Katreiz papildinot js vai css to dara failā assets/app.js vai assets/app.css tas viss sakompilējas vienā failā

Ja webpack.mixmix failā pieliek norādi uz citu direktoriju, kur ņemt js sourcu, tad tas paņem un piekompilē to klāt, piemēram:

.. code-block:: console

   ...

   // 1.
   mix.js('assets/js/app.js', 'static/webpack/js')

   // 2.
   mix.js('assets/js/alpine.js', 'static/webpack/js')

   ...

Rezumē:

.. code-block:: console

   npx mix - nokompilē jquery un bootstrap kopā uz 1.18 MiB

   npx mix --production nokompilē jquery un bootstrap kopā uz 248 KiB


Starpība liela

Finālā projekts šāds:

.. code-block:: console

   webpack
      ├── HOWTO.rst
      ├── assets
      │   ├── css
      │   │   └── app.css
      │   ├── js
      │   │   ├── app.js
      │   │   └── bootstrap.js
      │   └── scss
      │       └── app.scss
      ├── manage.py
      ├── mix-manifest.json
      ├── mysite
      │   ├── __init__.py
      │   ├── asgi.py
      │   ├── settings.py
      │   ├── urls.py
      │   └── wsgi.py
      ├── node_modules
      ├── package-lock.json
      ├── package.json
      ├── static
      │   └── mysite
      │       ├── css
      │       └── js
      ├── venv
      └── webpack.mix.js
