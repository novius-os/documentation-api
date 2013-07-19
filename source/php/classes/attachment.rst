.. _php/classes/attachment:

Attachment
##########

.. php:namespace:: Nos

.. php:class:: Attachment

	Binds a file to an object.

Configuration
*************

.. php:attr:: attached

	Required.
	The attached ID.

.. php:attr:: dir

	Required.
	Directory path, where the attachment is stored. Relative to :file:`local/data/files`.

.. php:attr:: alias

	An URL alias to access the directory path.

.. php:attr:: extensions

	Array of valid files extensions.

.. php:attr:: image

	If ``true``, accepts only files with an image extension. Same that ``extensions`` set to ``array('jpg', 'gif', 'png', 'jpeg')``.

.. php:attr:: check

    Used it to make the attachment private.
    A `callback function <http://php.net/manual/en/language.types.callable.php>`__ to check permissions against. It takes a single parameter: Attachement instance.

Methods
*******

.. php:staticmethod:: forge($attached, $config)

	:param string $attached: The attached ID.
	:param mixed $config: If is a ``string``, use it to load configuration array. ``Array`` otherwise:

		:dir: :php:attr:`Attachment::$dir`
		:alias: :php:attr:`Attachment::$alias`
		:extensions: :php:attr:`Attachment::$extensions`
		:image: :php:attr:`Attachment::$image`
		:check: :php:attr:`Attachment::$check`

	:returns: A new :php:class:`Nos\\Attachment`.

.. php:method:: newFile()

	:returns: Get the new attachment file path if one, ``false`` if no file exists.

.. php:method:: path()

	:returns: Get the attachment file path or ``false`` if no file exists.

.. php:method:: filename()

	:returns: Get the attachment filename or ``false`` if no file exists.

.. php:method:: extension()

	:returns: Get the attachment extension or ``false`` if no file exists.

.. php:method:: isImage()

	:returns: ``True`` if the Attachment is an image, ``false`` otherwise.

.. php:method:: url($absolute = true)

    :param bool $absolute: Default true, if false return relative URL
    :returns: Get the attachment url or ``false`` if no file exists.

.. php:method:: urlResized($max_width = 0, $max_height = 0, $absolute = true)

    :param array $max_width: Max width of the image.
    :param array $max_height: Max height of the image.
    :param bool $absolute: Default true, if false return relative URL
    :returns: Get the resized url for the Attachment  or ``false`` if no file exists or it's not an image.

.. php:method:: htmlAnchor($attributes = array())

    :param array $attributes: | Array of attributes to be applied to the anchor tag.
                              | If key 'text' is set in $attributes parameter, its value replace attachment filename
    :returns: Returns an HTML anchor tag with, by default, attachment URL in href and attachment filename in text.

.. php:method:: set($file, $filename = null)

	:param array $file: File path
	:param array $filename: File name
	:returns: Set a new Attachment file.
	:throws: \Fuel\Core\FileAccessException if new file have a not allowed extension.

.. php:method:: save()

	Save a new Attachment file

.. php:method:: delete()

	Delete the Attachment file

Example
*******

.. code-block:: php

	<?php

	$attachment = \Nos\Attachment::forge('my_id', array(
		'dir' => 'apps'.DS.'myapps',
		'alias' => 'myapps-attachment',
		'extensions' => array('pdf'),
		'check' => 'check_attachment',
	));

	// It's for example
	$_SESSION['user_connected'] = true;

	function check_attachment($attachment) {
		return $GLOBALS['user_connected'];
	}

	try {
		$attachment->set('/path/a_doc.doc');
	} catch (\Fuel\Core\FileAccessException $e) {
		// Exception will be throw, extension is doc, not a pdf.
	}

	$attachment->set('/path/a_pdf.pdf');
	$attachment->save();

	// Now file saved in local/data/files/apps/myapps/my_id/a_pdf.pdf

	echo $attachment->url();
	// Echo http://wwww.domain.ext/data/files/myapps-attachment/my_id/a_pdf.pdf

	$_SESSION['user_connected'] = false;
	// Now URL http://wwww.domain.ext/data/files/myapps-attachment/my_id/a_pdf.pdf return 404

	$attachment->delete();
