Model_Menu_Item
###############

.. php:namespace:: Nos\Menu

.. php:class:: Model_Menu_Item

	Extends :php:class:`Nos\\Orm\\Model`.

Relations
*********

.. php:attr:: parent

	* Relation type: :term:`belongs_to`.
	* Model: :php:class:`Model_Menu_Item`

.. php:attr:: children

	* Relation type: :term:`has_many`.
	* Model: :php:class:`Model_Menu_Item`

.. php:attr:: menu

	* Relation type: :term:`belongs_to`.
	* Model: :php:class:`Model_Menu`

Methods
*******

.. php:method:: html(array $params = array())

    :param array $params: Parameters array use by driver to renderer the item
    :returns: HTML representation of the item

.. php:method:: driver($reload = false)

	:param bool $reload: If true, reload the menu item driver
	:returns: The driver of the item
