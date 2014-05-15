Tools_Wysiwyg
#############

.. php:namespace:: Nos

.. php:class:: Tools_Wysiwyg

	Provides static methods to work with WYSIWYG.

::parse_wysiwyg()
-----------------

.. php:staticmethod:: parse($content)

    :param string $content: A :php:class:`Nos\\Model_Wysiwyg` content.
    :returns: Prepare wysiwyg content for display.

    | Replace enhancers by their content.
    | Replace :php:class:`Model_Page` and :php:class:`Model_Media` IDs by theirs URLs
    | Wysiwyg anchors are processed in case the href attribute begin with # :

        * If it begins with only one # then the href will be prefixed by the page url.
        * If if begins with two ## then it is transformed to only one #.
