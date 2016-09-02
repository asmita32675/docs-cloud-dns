.. _delete-delete-domains-and-subdomains-v1.0-account-domains:

Delete domains and subdomains
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code::

    DELETE /v1.0/{account}/domains

Deletes multiple domains and their subdomains from an account.

.. note::
   This call returns an asynchronous response, as described in
   :ref:`Synchronous and asynchronous responses<cdns-dg-synch-asynch>`.

This call deletes one or more specified domains from the account; when a domain
is deleted, its immediate resource records are also deleted from the account.
By default, if a deleted domain had subdomains, each subdomain becomes a root
domain and is not deleted; this can be overridden by the optional
``deleteSubdomains`` parameter. Utilizing the optional ``deleteSubdomains``
parameter on domains without subdomains does not result in a failure. When a
domain is deleted, any and all domain data is immediately purged and is not
recoverable via the API. So on a successful delete, subsequent requests for the
deleted object should return itemNotFound ( ``404`` ).

Transactionally, delete calls behave differently than other calls in that
deletes are never rolled back on exceptions, and multiple deletes in the same
request do not fail as a group. Instead, each delete is attempted even if one
or more fail. The response for a delete request in which one or more items fail
contains information regarding which items failed as well as information
regarding specific issues that caused the failure(s). See the examples that
follow.

In the previous two response examples, the requested domain objects could not
be deleted, because they were not found.

This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |Request is accepted.     |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|400 500                   |dnsFault                 |The DNS service has      |
|                          |                         |experienced a fault.     |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |You are not authorized   |
|                          |                         |to complete this         |
|                          |                         |operation. This error    |
|                          |                         |can occur if the request |
|                          |                         |is submitted with an     |
|                          |                         |invalid authentication   |
|                          |                         |token.                   |
+--------------------------+-------------------------+-------------------------+
|404                       |Not Found                |The requested item was   |
|                          |                         |not found.               |
+--------------------------+-------------------------+-------------------------+
|413                       |Over Limit               |The number of items      |
|                          |                         |returned is above the    |
|                          |                         |allowed limit.           |
+--------------------------+-------------------------+-------------------------+
|503                       |Service Unavailable      |The service is not       |
|                          |                         |available.               |
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |String                   |The tenant ID.           |
+--------------------------+-------------------------+-------------------------+

This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id1                       |String                   |id for the first domain. |
+--------------------------+-------------------------+-------------------------+
|id2                       |String                   |id for the next domain.  |
+--------------------------+-------------------------+-------------------------+
|deleteSubdomains          |String                   |If deleteSubdomains is   |
|                          |                         |true, also deletes       |
|                          |                         |subdomains. If false,    |
|                          |                         |subdomains are not       |
|                          |                         |deleted.                 |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example Delete domains and subdomains: XML request**


.. code::

   DELETE https://dns.api.rackspacecloud.com/v1.0/1234/domains?id=2725233&id=2725257&deleteSubdomains=true
   Accept: application/xml
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/xml
   Content-Length: 0

**Example Delete domains and subdomains: JSON request**


.. code::

   DELETE https://dns.api.rackspacecloud.com/v1.0/1234/domains?id=2725233&id=2725257&deleteSubdomains=true
   Accept: application/json
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/json
   Content-Length: 0

Response
--------

This operation does not return a response body.

