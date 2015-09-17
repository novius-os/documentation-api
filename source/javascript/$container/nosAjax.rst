nosAjax
#######

.. js:function:: $container.nosAjax(options)

	Performs an asynchronous HTTP (AJAX) request. This is a wrapper of `jQuery.ajax() <http://api.jquery.com/jQuery.ajax/>`__.

	:param JSON options:

		JSON that configure the AJAX request. Same that ``jQuery.ajax()`` with some differences:

		* Some defaults options.
		* Callback functions ``success`` and ``error`` are `monkey-patched <http://en.wikipedia.org/wiki/Monkey-Patch>`__
		  to execute defaults operations.

			* Function :js:func:`$container.nosAjaxSuccess` is automatically called if the request succeeds and return type is JSON.
			* Function :js:func:`$container.nosAjaxError` is automatically call if the request fails.

	.. code-block:: js

		$(domContext).nosAjax({
			dataType: 'json', // datatype is default 'json'.
			type: 'POST', // The request is made in POST by default.
			data: {}
		});

nosAjaxSuccess
##############

.. js:function:: $container.nosAjaxSuccess(options)

	Process JSON of a succeeded AJAX request.

	:param JSON options:

		:notify:        A ``string`` or ``{object}``. Use for call :js:func:`$.nosNotify`. If only a string is given, notification type will be 'notice', otherwise call $.nosNotify with the object parameters.
		:error:         A ``string`` or ``{object}``. Use for call :js:func:`$.nosNotify` with ``error`` for notification type.
		:action:        A ``string`` or ``{object}``. Use for call :js:func:`$container.nosAction`.
		:closeDialog:   ``Boolean``. If ``true``, call :js:func:`nosDialog.close`.
		:closeTab:      ``Boolean``. If ``true``, call :js:func:`nosTabs.close`.
		:replaceTab:    ``{}``. Use to call :js:func:`nosTabs.update`.
		:redirect:      ``string``. Redirect browser window to this URL.
		:dispatchEvent: Use to call :js:func:`$container.dispatchEvent`.
		:internal_server_error: Display error and backtrace in the browser console.

nosAjaxError
############

.. js:function:: $container.nosAjaxError(jqXHR, textStatus)

	Process a failed AJAX request.

	| Display the reconnection popup if the error comes to an end of the authentication session.
	| Display a notification otherwise.

	:param jqXHR jqXHR: An XMLHttpRequest object.
	:param string textStatus: Text status of the AJAX request.
