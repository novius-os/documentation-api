.. _php/configuration/template_variation:

Template variation
##################

The configuration of a template variation is assumed to be ``application_name::variation/template_name``.

:init: Optional. A callback function. Call to initialize a :php:class:`Nos\\Template\\Variation\\Model_Template_Variation`. Returns an array with fields names in keys and the initial values in values.
:admin: Array

    :layout: How the form, for item build with the driver, looks like and where fields are displayed inside it.
    :fields: All fields displayed in the form.

    .. seealso:: :ref:`php/configuration/crud`

:layout: Optional. A callback function. If exist, the return value overload the template configuration. Take the :php:class:`Nos\\Template\\Variation\\Model_Template_Variation` in parameter.
:cols: Optional. A callback function. If exist, the return value overload the template configuration. Take the :php:class:`Nos\\Template\\Variation\\Model_Template_Variation` in parameter.
:rows: Optional. A callback function. If exist, the return value overload the template configuration. Take the :php:class:`Nos\\Template\\Variation\\Model_Template_Variation` in parameter.
:file: Optional. A callback function. If exist, the return value overload the template configuration. Take the :php:class:`Nos\\Template\\Variation\\Model_Template_Variation` in parameter.
:screenshot: Optional. A callback function. If exist, the return value overload the template configuration. Take the :php:class:`Nos\\Template\\Variation\\Model_Template_Variation` in parameter.

.. seealso:: :ref:`metadata/templates`

.. code-block:: php

    <?php
    return array(
        'cols' => function($tpvar) {
            return int_val($tpvar->tpvar_data['cols']);
        },
        'admin' => array(
            'layout' => array(
                'content' => array(
                    'expander' => array(
                        'view' => 'nos::form/expander',
                        'params' => array(
                            'title'   => __('Configuration'),
                            'options' => array(
                                'allowExpand' => false,
                            ),
                            'content' => array(
                                'view' => 'nos::form/fields',
                                'params' => array(
                                    'fields' => array(
                                        'menus->principal->menu_id',
                                        'cols',
                                    ),
                                ),
                            ),
                        ),
                    ),
                ),
            ),
            'fields' => array(
                'menus->principal->menu_id' => array(
                    'label' => __('Menu'),
                    'renderer' => 'Nos\Renderer_Item_Picker',
                    'renderer_options' => array(
                        'model' => 'Nos\Menu\Model_Menu',
                        'appdesk' => 'admin/noviusos_menu/menu/appdesk',
                        'defaultThumbnail' => 'static/apps/noviusos_menu/img/64/menu.png',
                        'texts' => array(
                            'empty' => __('No menu selected'),
                            'add' => __('Pick a menu'),
                            'edit' => __('Pick another menu'),
                            'delete' => __('Un-select this menu'),
                        ),
                    ),
                ),
                'cols' => array(
                    'label' => __('Column number'),
                    'form' => array(
                        'type' => 'number',
                    ),
                ),
            ),
        ),
    );
