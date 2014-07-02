Menu_Item_Driver
################

.. php:namespace:: Nos\Menu

.. php:class:: Menu_Item_Driver

    This is an abstract class that must be extend by all declared drivers of :php:class:`Nos\\Menu\\Model_Menu_Item`.

    To declare a driver of :php:class:`Nos\\Menu\\Model_Menu_Item`, you have to extend the :file:`noviusos_menu::config` configuration file.

.. php:method:: title()

    :returns: The title of the :php:class:`Nos\\Menu\\Model_Menu_Item`

.. php:staticmethod:: html(array $params = array())

    | By default, if the driver have a key ``view`` in his config, this view is forged with 2 parameters ``params`` and ``item_driver``
    | If the driver have no view, build a ``div`` tag with ``html_tag`` function with ``$params`` and the driver title in parameters

    :param array $params: Array of parameters
    :returns: A HTML representation of the :php:class:`Nos\\Menu\\Model_Menu_Item`


.. php:staticmethod:: config($reload = false)

    The config file is assumed to be ``application_name::driver_path``.

    :param bool $reload: If ``true``, reload the configuration and not use cache
    :returns array: The configuration of the driver

    .. seealso:: :ref:`Menu item driver configuration <php/configuration/menu_item_driver>`.
