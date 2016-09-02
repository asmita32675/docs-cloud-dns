.. _get-list-ptr-records-v1.0-account-rdns-service-name:

List PTR records
~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/rdns/{service-name}

Lists all PTR records configured for a specified Cloud device.

This call lists all PTR records configured for a specified Cloud device.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request is missing   |
|                          |                         |one or more elements, or |
|                          |                         |the values of some       |
|                          |                         |elements are invalid.    |
+--------------------------+-------------------------+-------------------------+
|500                       |dnsFault                 |The DNS service has      |
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
|{service-name}            |String                   |Name of the Cloud        |
|                          |                         |service.                 |
+--------------------------+-------------------------+-------------------------+

This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|href                      |String                   |Device-resource-uri for  |
|                          |                         |the specified Cloud      |
|                          |                         |device.                  |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example List PTR records: XML request**

.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/rdns/cloudServersOpenStack?href=https://dfw.servers.api.rackspacecloud.com/v2/1234/servers/0987654321
   Accept: application/xml
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/xml
   Content-Length: 0

**Example List PTR records: JSON request**

.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/rdns/cloudServersOpenStack?href=https://dfw.servers.api.rackspacecloud.com/v2/1234/servers/0987654321
   Accept: application/json
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/json
   Content-Length: 0

Response
--------

**Example List PTR records: XML response**

.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/xml
   Content-Length: 710

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <rdns xmlns:ns2="http://www.w3.org/2005/Atom" xmlns="http://docs.rackspacecloud.com/dns/api/v1.0" xmlns:ns3="http://docs.rackspacecloud.com/dns/api/management/v1.0">
       <ns2:link href="https://dfw.servers.api.rackspacecloud.com/v2/1234/servers/0987654321" rel="cloudServersOpenStack"></ns2:link>
       <recordsList>
           <record id="PTR-000000" type="PTR" name="example.com" data="192.0.2.6" ttl="56000" updated="2011-06-24T01:12:51Z" created="2011-06-24T01:12:51Z"/>
           <record id="PTR-000001" type="PTR" name="example.com" data="2001:db8::6" ttl="56000" updated="2011-06-24T01:12:51Z" created="2011-06-24T01:12:51Z"/>
       </recordsList>
   </rdns>

**Example List PTR records: JSON response**

.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/json
   Content-Length: 680

   {
     "recordsList" : {
       "records" : [ {
         "name" : "example.com",
         "id" : "PTR-000000",
         "type" : "PTR",
         "data" : "192.0.2.6",
         "updated" : "2011-06-24T01:12:51.000+0000",
         "ttl" : 56000,
         "created" : "2011-06-24T01:12:51.000+0000"
       }, {
         "name" : "example.com",
         "id" : "PTR-000001",
         "type" : "PTR",
         "data" : "2001:db8::6",
         "updated" : "2011-06-24T01:12:51.000+0000",
         "ttl" : 56000,
         "created" : "2011-06-24T01:12:51.000+0000"
       } ]
     },
     "link" : {
       "content" : "",
       "href" : "https://dfw.servers.api.rackspacecloud.com/v2/1234/servers/0987654321",
       "rel" : "cloudServersOpenStack"
     }
   }




