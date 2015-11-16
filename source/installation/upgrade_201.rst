###########################
Upgrade dari 2.0.0 ke 2.0.1
###########################

Before performing an update you should take your site offline by
replacing the index.php file with a static one.

Step 1: Update your CodeIgniter files
=====================================

Replace all files and directories in your "system" folder and replace
your index.php file. If any modifications were made ke your index.php
they will need ke be made fresh in this new one.

.. note:: If you have any custom developed files in these folders please
	make copies of them first.

Step 2: Replace config/mimes.php
================================

This config file has been updated ke contain more mime types, please
copy it ke application/config/mimes.php.

Step 3: Check for forms posting ke default controller
=====================================================

The default behavior for form_open() when called with no parameters
used ke be ke post ke the default controller, but it will now just leave
an empty action="" meaning the form will submit ke the current URL. If
submitting ke the default controller was the expected behavior it will
need ke be changed from::

	echo form_open(); //<form action="" method="post" accept-charset="utf-8">

ke use either a / or base_url()::

	echo form_open('/'); //<form action="http://example.com/index.php/" method="post" accept-charset="utf-8">
	echo form_open(base_url()); //<form action="http://example.com/" method="post" accept-charset="utf-8">

