.. _php/constants:

Constants
#########

All native constants of FuelPHP are available but links to specific Novius OS directories.

.. seealso::

	`FuelPHP native constants documentation <http://fuelphp.com/docs/general/constants.html>`_.

.. php:const:: NOSROOT

	Path where Novius OS is installed.

.. php:const:: PUBLIC_DIR

    Contains the name of the public directory. Initialized to ``public`` if not set.

    .. versionadded:: 4.2

.. php:const:: NOSPATH

	Path of Novius OS core: :file:`NOSROOT/novius-os/framework/`.

.. php:const:: APPPATH

	Overload of the native FuelPHP's constant. Path to the application directory: :file:`NOSROOT/local/`.

.. php:const:: COREPATH

	Overload of the native FuelPHP's constant. Path to the FuelPHP core directory: :file:`NOSROOT/novius-os/fuel-core/`.

.. php:const:: DOCROOT

	Overload of the native FuelPHP's constant. Path to the location where the `startup script` is: :file:`NOSROOT/public/`.

.. php:const:: PKGPATH

	Overload of the native FuelPHP's constant. Path to the packages directory: :file:`NOSROOT/novius-os/packages/`.
