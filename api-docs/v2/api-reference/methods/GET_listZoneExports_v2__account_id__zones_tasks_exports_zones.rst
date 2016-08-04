.. _GET_listZoneExports_v2__account_id__zones_tasks_exports_zones:

List zone exports
-----------------

.. code::

    GET /v2/{TENANT_ID}/zones/tasks/exports

This operation lists all of the zone exports created by this account. Returned
objects can be queried by using the links in the ``links`` field.

This table shows the possible response codes for this operation:

+---------+---------------------+---------------------------------------------+
| Response| Name                | Description                                 |
| code    |                     |                                             |
+=========+=====================+=============================================+
| 200     | Accepted            | The request was accepted for  processing,   |
|         |                     | but the processing has not completed.       |
+---------+---------------------+---------------------------------------------+
| 401     | Unauthorized        | You are not authorized to complete this     |
|         |                     | operation. This error can occur if the      |
|         |                     | request is submitted with an invalid        |
|         |                     | authentication token.                       |
+---------+---------------------+---------------------------------------------+
| 404     | Not Found           | The requested item was not found.           |
+---------+---------------------+---------------------------------------------+

Request
^^^^^^^

This table shows the URI parameters for the request:

+---------------------+---------+---------------------------------------------+
| Name                | Type    | Description                                 |
+=====================+=========+=============================================+
| ``{TENANT_ID}``     | ​String | The account ID of the account owner.        |
+---------------------+---------+---------------------------------------------+


**Example: List zone exports, request**

.. code::

    GET /v2/123456/zones/tasks/exports/ HTTP/1.1
    Host: global.dns.rackspacecloud.com
    Accept: application/json

This operation does not accept a request body.

Response
^^^^^^^^

This table shows the body parameters for the response:

+--------------------------------+---------------------+----------------------+
|Name                            |Type                 |Description           |
+================================+=====================+======================+
|**exports**                     |Array                |An array of zones     |
|                                |                     |exports.              |
+--------------------------------+---------------------+----------------------+
|exports.\ **id**                |Uuid                 |The ID of the zone    |
|                                |                     |export.               |
+--------------------------------+---------------------+----------------------+
|exports.\ **zone_id**           |Uuid                 |The ID of the zone.   |
+--------------------------------+---------------------+----------------------+
|exports.\ **project_id**        |Integer              |The project, account, |
|                                |                     |or tenant ID.         |
+--------------------------------+---------------------+----------------------+
|exports.\ **location**          |String               |The location of the   |
|                                |                     |zone export.          |
+--------------------------------+---------------------+----------------------+
|exports.\ **message**           |String               |A description of the  |
|                                |                     |zone export.          |
+--------------------------------+---------------------+----------------------+
|exports.\ **version**           |Integer              |The version of the    |
|                                |                     |zone export.          |
+--------------------------------+---------------------+----------------------+
|exports.\ **created_at**        |Datestamp            |The time stamp        |
|                                |                     |indicating the        |
|                                |                     |creation date of the  |
|                                |                     |zone export.          |
+--------------------------------+---------------------+----------------------+
|exports.\ **updated_at**        |Datestamp            |The time stamp        |
|                                |                     |indicating the date   |
|                                |                     |that the zone export  |
|                                |                     |was last updated.     |
+--------------------------------+---------------------+----------------------+
|exports.\ **links**             |Object               |A container with the  |
|                                |                     |links to the zone.    |
+--------------------------------+---------------------+----------------------+
|exports.links.\ **self**        |Uuid                 |The link to the zone. |
+--------------------------------+---------------------+----------------------+
|**links**                       |Object               |A container with the  |
|                                |                     |links to the exports. |
+--------------------------------+---------------------+----------------------+
|links.\ **self**                |Uuid                 |The link to the       |
|                                |                     |zone exports.         |
+--------------------------------+---------------------+----------------------+
|**metadata**                    |Object               |Any metadata key and  |
|                                |                     |value pairs.          |
+--------------------------------+---------------------+----------------------+
|metadata.\ **total_count**      |Integer              |The number of exported|
|                                |                     |zones in the array.   |
+--------------------------------+---------------------+----------------------+

**Example: List zone exports, response**

.. code::

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "exports": [
            {
                "status": "COMPLETE",
                "zone_id": "30ea7692-7f9e-4195-889e-0ba11620b491",
                "links": {
                    "self": "https://global.dns.rackspacecloud.com/v2/123456/zones/tasks/exports/d2f36aa6-2da4-4b22-a2a9-9cdf19a2f248",
                    "export": "https://global.dns.rackspacecloud.com/v2/123456/zones/30ea7692-7f9e-4195-889e-0ba11620b491/tasks/exports/d2f36aa6-2da4-4b22-a2a9-9cdf19a2f248/export"
                },
                "created_at": "2015-08-24T19:46:50.000000",
                "updated_at": "2015-08-24T19:46:50.000000",
                "version": 2,
                "location": "https://global.dns.rackspacecloud.com/v2/123456/zones/30ea7692-7f9e-4195-889e-0ba11620b491/tasks/exports/d2f36aa6-2da4-4b22-a2a9-9cdf19a2f248/export",
                "message": null,
                "project_id": "123456",
                "id": "d2f36aa6-2da4-4b22-a2a9-9cdf19a2f248"
            },
            {
                "status": "COMPLETE",
                "zone_id": "0503f9fd-3938-47a4-bbf3-df99b088abfc",
                "links": {
                    "self": "https://global.dns.rackspacecloud.com/v2/123456/zones/tasks/exports/3d7d07a5-2ce3-458e-b3dd-6a29906234d8",
                    "export": "https://global.dns.rackspacecloud.com/v2/123456/zones/tasks/exports/3d7d07a5-2ce3-458e-b3dd-6a29906234d8/export"
                },
                "created_at": "2015-08-25T15:16:10.000000",
                "updated_at": "2015-08-25T15:16:10.000000",
                "version": 2,
                "location": "https://global.dns.rackspacecloud.com/v2/123456/zones/tasks/exports/3d7d07a5-2ce3-458e-b3dd-6a29906234d8/export",
                "message": null,
                "project_id": "123456",
                "id": "3d7d07a5-2ce3-458e-b3dd-6a29906234d8"
            },
        ],
        "links": {
            "self": "https://global.dns.rackspacecloud.com/v2/123456/zones/tasks/exports"
        },
        "metadata": {
            "total_count": 2
        }
    }
