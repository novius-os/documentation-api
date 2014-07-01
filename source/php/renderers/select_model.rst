Select Model
##############

.. php:namespace:: Nos

.. php:class:: Renderer_Select_Model

    | Extends :php:class:`Nos\\Renderer`.
    | This renderer is used to display a ``select`` tag fill with items from a model.
    | This renderer manage automatically behaviours :php:class:`Twinnable <Nos\\Orm_Behaviour_Contextable>` and :php:class:`Twinnable <Nos\\Orm_Behaviour_Twinnable>`
    | The select is refresh automatically if an item of the model ise created, saved or deleted.

Configuration
*************

.. php:attr:: model

	The name of the model

.. php:attr:: multiple

	Set to ``true`` if you want to select multiple items. Default ``false``.

.. php:attr:: empty_option

	Set to ``true`` if you want an empty option in select. Default ``true``.

.. php:attr:: choose_label

	The label of the empty option. Default empty.

Example
*******

Adding a select model on page in a CRUD form configuration:

.. code-block:: php

    <?php

    return array(
        'label' => __('Location:'),
        'renderer' => 'Nos\Renderer_Select_Model',
        'renderer_options' => array(
            'model' => 'Nos\Page\Model_Page',
        ),
    );
