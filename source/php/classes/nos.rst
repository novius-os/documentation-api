Nos
####

.. php:namespace:: Nos

.. php:class:: Nos

	Provides static methods useful in Novius OS.


Entry points
------------

.. php:attr:: entry_point

	The Novius OS entry point. Equal to one of the following constants.

.. php:const:: ENTRY_POINT_ADMIN
.. php:const:: ENTRY_POINT_FRONT
.. php:const:: ENTRY_POINT_404
.. php:const:: ENTRY_POINT_INSTALL
.. php:const:: ENTRY_POINT_OIL

.. versionadded:: 0.2.0.1

.. _php/classes/nos/main_controller:

::main_controller()
-------------------

.. php:staticmethod:: main_controller()

	:returns: Instance of the main :term:`controller <Controller>`.

::hmvc()
--------

.. php:staticmethod:: hmvc($where, $args = null)

	:param mixed $where: Route for the request.
	:param array $args: The method parameters.

	Executes an :term:`HMVC` request.
