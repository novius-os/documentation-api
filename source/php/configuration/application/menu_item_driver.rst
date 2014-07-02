.. _php/configuration/menu_item_driver:

Menu item driver
################

:name: The name of the driver
:texts: Array

    :add: Label of the add button for the driver
    :new: Label for a new item build with the driver

:attributes: Array of EAV attributes save in the :php:class:`Nos\\Menu\\Model_Menu_Item`
:icon: URL of the icon representing the driver
:view: Optional. Path of the view use to display an item build with the driver

    .. seealso:: :php:meth:`Nos\\Menu\\Menu_Item_Driver::html`

:admin: Array

    :layout: How the form, for item build with the driver, looks like and where fields are displayed inside it.
    :fields: All fields displayed in the form.

    .. seealso:: :ref:`php/configuration/crud`

.. code-block:: php

    <?php
    return array(
        'name' => __('Link to a page'),
        'texts' => array(
            'add' => __('Add a new link to a page'),
            'new' => __('New link to a page'),
        ),
        'icon' => 'static/apps/noviusos_menu/img/16/page.png',

        'attributes' => array(
            'page_id',
        ),

        'view' => 'noviusos_menu::driver/page',

        'admin' => array(
            'layout' => array(
                'standard' => array(
                    'view'   => 'nos::form/accordion',
                    'params' => array(
                        'accordions' => array(
                            'main' => array(
                                'fields' => array(
                                    'mitem_page_id',
                                ),
                            ),
                        ),
                    ),
                ),
                array(
                    'view'   => 'noviusos_menu::admin/driver/page',
                ),
            ),
            'fields' => array(
                'mitem_page_id' => array(
                    'label' => __('Page:'),
                    'form' => array(
                        'type' => 'hidden',
                        'class' => 'menu_item_page_id',
                    ),
                    'renderer' => 'Nos\Renderer_Item_Picker',
                    'renderer_options' => array(
                        'model' => 'Nos\Page\Model_Page',
                        'appdesk' => 'admin/noviusos_page/appdesk',
                        'defaultThumbnail' => 'static/apps/noviusos_page/img/64/page.png',
                        'texts' => array(
                            'empty' => __('No page selected'),
                            'add' => __('Pick a page'),
                            'edit' => __('Pick another page'),
                            'delete' => __('Un-select this page'),
                        ),
                    ),
                ),
            ),
        ),
    );
