.. _faults:

======
Faults
======

API operations that return an error return one of the fault objects described
in this section.  All fault objects extend from the base fault,
``serviceFault``, for easier exception handling  for languages that support it.

The following table lists possible error types with their associated error
codes and descriptions.

.. list-table::
   :widths: 25 6 59
   :header-rows: 1

   * - Error type
     - Error code
     - Description
   * - Service Unavailable
     - 503
     - The request could not be processed because back-end services were
       temporarily unavailable. This condition should be temporary; contact
       support if the error persists.
   * - unauthorized
     - 401
     - The user is not authorized to access the API functionality in question.
       The user may not have authenticated to the API. If the user should have
       access to the API functionality, contact support.
   * - bad_request
     - 400
     - The request is missing one or more elements, or the values of some
       elements are invalid. See the errors or type elements for specific
       information.
   * - forbidden
     - 403
     - The endpoint is not defined in the service catalog, or the user is not
       permitted to perform the API action in question.
   * - resource_not_found
     - 404
     - The back-end services did not find anything matching the request UUID.
   * - method_not_allowed
     - 405
     - The method is not allowed for the URL.
   * - over_quota
     - 413
     - The request has exceeded the rate limit or quota. Contact support if you
       think you need higher limits.
   * - duplicate_resource
     - 409
     - The back-end services could not complete the request due to a conflict
       with the current state of the resource. Possibly, the user is trying to
       create an entity that already exists. See the message element for
       specifics.
   * - timeout
     - 504
     - The back-end services encountered an unexpected condition that prevented
       them from fulfilling the request in the allotted time.
   * - Internal Server Error
     - 500
     - The back-end services encountered an unexpected condition that prevented
       them from fulfilling the request. See the details element for specific
       information.

All error responses have the following elements:

- The ``code`` element shows the HTTP error code.
- The ``type`` element shows the type of error.
- The ``request_id`` helps API operators debug the request in a support ticket,
  if necessary.
- The ``message`` field, when present, informs the user of the exact problem
  that the API detected.

**Example: Error response**

.. code::

    {
      "code" : 500,
      "type" : "error",
      "request_id": "req-6d896f1e-9686-454e-af6f-412a802f9451"
    }


The following ``bad_request`` example shows validation errors:

**Example: bad_request error caused by validation errors**

.. code::

    {
      "code":400,
      "type": "invalid_object",
      "errors": {
         "errors": [
            {
               "path": [ "name" ],
               "message": "u'example.com' is not a 'domainname'",
               "validator": "format",
               "validator_value": "domainname"
            }
         ]
      },
      "request_id": "req-9ebcb6a5-5673-4696-bbfc-61524e986f31"
    }