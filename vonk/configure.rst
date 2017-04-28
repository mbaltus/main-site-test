.. _configure:

===========================
Configuring the Vonk server
===========================

In this section we assume you have downloaded and installed the Vonk binaries. If not, please see 
the :ref:`previous section <getting-started>` and follow the steps there first.

The steps you followed to get started will provide you with a basic Vonk server,
that runs on a standard port and keeps the data in memory.

If you need to adjust the port, or want to use a MongoDB or SQL database, you can
configure Vonk by adjusting the :code:`hosting.json` and :code:`appsettings.json` file.
If you want to change the way Vonk logs its information, you can adjust :code:`logsettings.json`.
On this page you can read how to change the settings.


Changing the port number
------------------------
By default Vonk will run on port 4080 of your system. You can change the port setting in the :code:`hosting.json` file that is part
of the Vonk distribution:

*	Navigate to the location where you extracted the Vonk files
*	In a text editor open :code:`hosting.json` to find this setting:

.. code-block:: json

   {
      "urls": "http://*:4080"
   }

*	Change the number to the port number you want


Using a different repository
----------------------------
The default setting for Vonk is to run in memory. You will probably want to change this to use your own database.
You can use either a MongoDB or a SQL server database with Vonk.

Using MongoDB
^^^^^^^^^^^^^


Using SQL server
^^^^^^^^^^^^^^^^


Changing from http to https
---------------------------
If you need your server to run on https instead of http, follow these steps:

*	Navigate to the location where you extracted the Vonk files.
*	Open :code:`appsettings.json` in a text editor and find these settings:

.. code-block:: json

   {
      "UseHttps": "false",
      "CertificateFile": "iis_dev.pfx",
   }


*	Change the setting for :code:`UseHttps` from ``false`` to ``true``
*	Set :code:`CertificateFile` to the location of the `.pfx` file that contains the certificate for your site
*	Edit :code:`hosting.json` and change the ``urls`` setting to include https for the port number you want. For example:

.. code-block:: json

   {
      "urls": "http://*:4080;https://*:5080"
   }


*	Before starting the server, set an environment variabele on your system to contain the password of the `.pfx` file:

	+ In Powershell run: :code:`$env:VONK_vonk_certificate_password="my_password"`, where `my_password` is the password
	  for the `.pfx` file
	+ or go to your `System`, open the `Advanced system settings` --> `Environment variables` and create a new variable
	  with the name :code:`VONK_vonk_certificate_password` and the value set to your password


   

Configuring log settings
------------------------