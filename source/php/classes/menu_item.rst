Menu_Item
#########

.. php:namespace:: Nos\Menu

.. php:class:: Menu_Item

    This class is use to build :php:class:`Nos\\Menu\\Menu_Item_Driver`.

.. php:staticmethod:: forge($item)

    :param mixed $item: Can be:

                        * a :php:class:`Nos\\Menu\\Model_Menu_Item` instance
                        * a int for :php:class:`Nos\\Menu\\Model_Menu_Item` ID
                        * or a string for the driver name of a new :php:class:`Nos\\Menu\\Model_Menu_Item` instance

    :returns: A :php:class:`Nos\\Menu\\Menu_Item_Driver`, driver of the :php:class:`Nos\\Menu\\Model_Menu_Item` in entrance

.. php:staticmethod:: drivers()

    :returns: An array of all available :php:class:`Nos\\Menu\\Menu_Item_Driver`. Driver name in key, driver configuration in value.
