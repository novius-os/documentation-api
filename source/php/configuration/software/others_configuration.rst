.. _php/configuration/software:

Novius OS
#########

A sample configuration file is available in :file:`local/config/config.php.sample`.
Just rename (or copy) it to :file:`local/config/config.php`, and update it to your case.

.. php:global:: cache

    ``Boolean`` for use of cache on front. By default is ``true``, except in DEVELOPMENT environment.

    .. versionadded:: 0.2.0.2

.. php:global:: cache_duration_page

    ``Int``, number of seconds of cache validity. By default is ``60``.

.. php:global:: cache_model_properties

    ``Boolean`` for use of cache on :php:class:`Nos\\Orm\\Model` properties. By default is ``false``.
    If is ``true``, all models properties will be cached with a auto-refresh mechanism : if you add a column on a model which has properties defined,
    the cache will be refreshed by a DB ``list_columns`` request when you access this column with ``get()`` or ``set()``.

    .. versionadded:: Chiba 1.0.1

.. php:global:: upload

    ``Array`` :

    :param disabled_extensions: ``Array`` of invalid extensions for files uploaded in Novius OS. By default ``php`` is disabled.

.. php:global:: assets_minified

    ``Boolean`` for use of assets minified in back-office. By default is ``true``, except in DEVELOPMENT environment.

.. php:global:: temp_dir

    Path of a temp directory. Set to :file:`local/data/temp` by default.

.. _php/configuration/software/db:

Database
########

The DB configuration was initially created by the installation wizard. But you can (and you must to go live) update
it after installation.

The DB configuration is in :file:`local/config/db.php`.

 .. seealso::

 	`FuelPHP Database documentation <http://fuelphp.com/docs/classes/database/introduction.html>`_ for details.

Email
#####

By default, your Novius OS is not configured to send mail, because it's too dependent on the server.

A sample configuration file is available in :file:`local/config/email.config.php.sample`.
Just rename (or copy) it to :file:`local/config/email.config.php`, and update it to your case.

.. seealso::

	`FuelPHP email package documentation <http://fuelphp.com/docs/packages/email/introduction.html>`_ for details.

.. _php/configuration/wysiwyg:

WYSIWYG
#######

You can modify default configuration of WYSIWYGs in your Novius OS.
You can also have multiple configurations, especially configurations for :doc:`contexts <multi_context>`.

A sample configuration file is available in :file:`local/config/wysiwyg.config.php.sample`.
Just rename (or copy) it to :file:`local/config/wysiwyg.config.php`, and update it to your case.

To set a configuration for a context, set a key with the context id in the array ``setups``:

.. code-block:: php

    <?php
    return array(
        'default' => array(
        ),

        'active_setup' => 'default',

        'setups' => array(
            'default' => array(),
            'main::en_GB' => array(
                //... Set here your specific configuration for context main::en_GB
            ),
            //'main::fr_FR' => array(),
            //'main::ja_JP' => array(),
        ),
    );


.. seealso::

	`TinyMCE documentation <http://www.tinymce.com/wiki.php>`_ for details.

.. _php/configuration/friendly_slug:

Friendly slug
#############

All segments of URLs builded in Novius OS are cleaned by the friendly slug mechanism.

A sample configuration file is available in :file:`local/config/friendly_slug.config.php.sample`.
Just rename (or copy) it to :file:`local/config/friendly_slug.config.php`, and update it to your case.

:active_setup: The active setup key. This key must be present in ``setups``. Execute in all case. Default value: ``default``.
:setups:       Array of different setups.

In ``setups``, key can be a context ID. In this case, this setup is excute for slugs in this context.

Four setups of rules are defined:

* ``default`` setup. All characters ``?``, ``:``, ``\``, ``/``, ``#``, ``[``, ``]``, ``@``, ``&`` and space are replaced by ``-``.
  Transform to lower case. Remove trailing ``-``. Replace multiple ``-`` by one.
* ``no_accent`` setup. All accent characters are replaced by the equivalent character without accent.
* ``no_special`` setup. All characters that are not a word character, a ``-`` or a ``_`` are replaced by ``-``.
* ``no_accent_and_special`` setup. Combination of ``no_accent`` and ``no_special`` setups.

A setup value is an array. This array can contains :

* an other setup ID
* A ``key => value``, in this case, all occurrence of ``key`` in the slug are replaced by ``value``.
* Value can be also an array, with a key ``replacement`` and a key ``flags`` for the regular expression.

Sample:

.. code-block:: php

    <?php
    return array(
        'setups' => array(
            'my_default' => array(
                // Use the 'no_accent' setup
                'no_accent',

                // Replace space by '_'
                ' ' => '_',

                 // All characters that are not a word character, a '-' or a '_' or a '*' are replaced by '-'.
                '[^\w\*\-_]' => array('replacement' => '-', 'flags' => 'i'),
            ),
        ),
    );

