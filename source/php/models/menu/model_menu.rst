Model_Menu
##########

.. php:namespace:: Nos\Menu

.. php:class:: Model_Menu

	Extends :php:class:`Nos\\Orm\\Model`.

Relations
*********

.. php:attr:: items

	* Relation type: :term:`has_many`.
	* Model: :php:class:`Model_Menu_Item`

Behaviours
**********

* :php:class:`Twinnable <Nos\\Orm_Behaviour_Twinnable>`

Methods
*******

.. php:method:: html(array $params = array())

    :param array $params: the parameters array:

        :view: The view path to use. Default: ``noviusos_menu::menu``

    :returns: A View forged with ``$params``

.. php:method:: branch($parent = null)

	:param mixed $parent: If null, return the root branch. Can be a :php:class:`Model_Menu_Item`, then return his branch.
	:returns: Array of :php:class:`Model_Menu_Item`

.. php:staticmethod:: buildFromPages($context, $page_id = null, $depth = -1)

    Build a :php:class:`Model_Menu` where items reproduce the pages tree of the context.

    :param string $context: The context ID
    :param mixed $page_id: The root page ID, can be null
    :param int $depth: The depth of the menu. Default: ``-1``, unlimited.
    :returns: Array of :php:class:`Model_Menu_Item`

