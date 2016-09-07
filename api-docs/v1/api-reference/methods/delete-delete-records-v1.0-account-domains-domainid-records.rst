.. _delete-delete-records-v1.0-account-domains-domainid-records:

Delete records
~~~~~~~~~~~~~~

.. code::

    DELETE /v1.0/{account}/domains/{domainId}/records

Deletes multiple records from the domain.

.. note::
   This call returns an asynchronous response, as described in
   :ref:`Synchronous and asynchronous responses<cdns-dg-synch-asynch>`.

These calls delete a specified record or multiple records from a specified
domain.

When a record is deleted, any and all record data is immediately purged and is
not recoverable via the API. So on a successful delete, subsequent requests for
the deleted record should return itemNotFound ( ``404`` ).

Transactionally, delete calls behave differently than other calls in that
deletes are never rolled back on exceptions, and multiple deletes in the same
request do not fail as a group. Instead, each delete is attempted even if one
or more fail. The response for a delete request in which one or more items fail
contains information regarding which items failed as well as information
regarding specific issues that caused the failure(s). See the examples that
follow.

In the previous two response examples, the requested record objects could not
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
|{domainId}                |String                   |ID for the domain.       |
+--------------------------+-------------------------+-------------------------+

This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id1                       |String                   |ID for the first record. |
+--------------------------+-------------------------+-------------------------+
|id2                       |String                   |ID for the next record.  |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example Delete records: XML request**


.. code::

   DELETE https://dns.api.rackspacecloud.com/v1.0/1234/domains/2725233/records/?
   id=A-6817754&id=111111111&id=222222222&id=NS-6251982
   Accept: application/xml
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/xml
   Content-Length: 0

**Example Delete records: JSON request**


.. code::

   DELETE https://dns.api.rackspacecloud.com/v1.0/1234/domains/2725233/records/?
   id=A-6817754&id=111111111&id=222222222&id=NS-6251982
   Accept: application/json
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/json
   Content-Length: 0

**Example Delete records failure: XML response**


.. code::

   Status: 202 Accepted
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/xml
   Content-Length: 737

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <deletefault code="500" xmlns:ns2="http://www.w3.org/2005/Atom" xmlns="http://docs.rackspacecloud.com/dns/api/v1.0" xmlns:ns3="http://docs.rackspacecloud.com/dns/api/management/v1.0">
       <message>One or more items could not be deleted.</message>
       <details>See errors list for details.</details>
       <failedItems>
           <fault code="404">
               <message>Object not Found.</message>
               <details>Domain ID: 2720150; Record ID: 111111111</details>
           </fault>
           <fault code="404">
               <message>Object not Found.</message>
               <details>Domain ID: 2720150; Record ID: 222222222</details>
           </fault>
       </failedItems>
   </deletefault>

**Example Delete records failure: JSON response**


.. code::

   Status: 202 Accepted
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/json
   Content-Length: 422

   {
     "failedItems" : {
       "faults" : [ {
         "message" : "Object not Found.",
         "code" : 404,
         "details" : "Domain ID: 2720150; Record ID: 111111111"
       }, {
         "message" : "Object not Found.",
         "code" : 404,
         "details" : "Domain ID: 2720150; Record ID: 222222222"
       } ]
     },
     "message" : "One or more items could not be deleted.",
     "code" : 500,
     "details" : "See errors list for details."
   }

Response
--------

This operation does not return a response body.

