Model_Template_Variation
########################

.. php:namespace:: Nos\Template\Variation

.. php:class:: Model_Template_Variation

	Extends :php:class:`Nos\\Orm\\Model`.

Relations
*********

.. php:attr:: pages

	* Relation type: :term:`has_many`.
	* Model: :php:class:`Nos\\Page\\Model_Page`

Providers
*********

.. php:attr:: menus

	* Model: :php:class:`Nos\\Menu\\Model_Menu`

Behaviours
**********

* :php:class:`Contextable <Nos\\Orm_Behaviour_Contextable>`
* :php:class:`Author <Nos\\Orm_Behaviour_Author>`

Methods
*******

.. php:method:: configCompiled($reload = false)

    :param bool $reload: If true, reload the variation config
    :returns: Returns the configuration array of the template variation.

.. php:method:: templateConfig()

    :returns: Returns the configuration array of the template use by the variation.

.. php:staticmethod:: getTemplateVariationDefault($context)

    :param string $context: The context ID
    :returns: The default :php:class:`Model_Template_Variation` for this context
