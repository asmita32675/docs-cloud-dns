.. _curl-listing-zone:

Getting details about a zone with cURL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use this API operation to get detailed output for a specific zone. This
operation does not require a request body.

The following example shows the cURL request for list zone:

**Example: List zone, cURL request**

.. code::

    curl -s  \
    -H "X-Auth-Token: $AUTH_TOKEN" \
    -H "Accept: application/json"  \
    https://global.dns.api.rackspacecloud.com/v2/$TENANT_ID/zones/{zoneId} | python -m json.tool

Remember to replace the values in the example with actual values.

-  **AUTH_TOKEN**

	The token that you received during authentication.  For automatic
	replacement, set your environment variables (see
	:ref:`Configure environment variables <configure-environment-variables>`).


-  **TENANT_ID**

   Your Rackspace Cloud account ID.  For automatic  replacement, set your
   environment variables (see
   :ref:`Configure environment variables <configure-environment-variables>`).

-  **zoneId**

	The ID returned in the create zone response.

The following example shows the response:

**Example List zone response**

.. code::

    HTTP/1.1 200 OK
    Vary: Accept
    Content-Type: application/json

    {
        "id": "a86dba58-0043-4cc6-a1bb-69d5e86f3ca3",
        "pool_id": "572ba08c-d929-4c70-8e42-03824bb24ca2",
        "project_id": "123456",
        "name": "example.org.",
        "email": "joe@example.org.",
        "ttl": 7200,
        "serial": 1404757531,
        "status": "ACTIVE",
        "description": "This is an example zone.",
        "masters": [],
        "type": "PRIMARY",
        "transferred_at": null,
        "version": 1,
        "created_at": "2015-06-18T18:25:31.275934",
        "updated_at": null,
        "links": {
          "self": "https://global.dns.api.rackspacecloud.com/v2/123456/zones/a86dba58-0043-4cc6-a1bb-69d5e86f3ca3"
        }
    }

The response shows that the zone has been created and has a status of
``ACTIVE``.

..  note::

    If you have multiple zones or records and want to get a subset of them, you
    could paginate, sort or filter the results. See
    :ref:`Pagination and sorting<paginated-collections>`
    or :ref:`Filtering<filtering>` for more information.

