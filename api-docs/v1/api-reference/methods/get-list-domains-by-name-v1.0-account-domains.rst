.. _get-list-domains-by-name-v1.0-account-domains:

List domains by name
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1.0/{account}/domains

Filters domains by domain name: list all domains manageable by the account
specified that exactly match the value of the ``name`` parameter.

Note that you can use the query parameter ``name`` to filter domains by domain
name: list all domains manageable by the account specified that exactly match
the fully qualified value of the ``name`` parameter. Note that if there is no
exact match, no results are returned.

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
|name                      |String                   |Name of the domain to    |
|                          |                         |find.                    |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

**Example Filter by Fully Qualified domain Name: XML request**


.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/domains?name=region2.example.net
   Accept: application/xml
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/xml
   Content-Length: 0


**Example Filter by Fully Qualified domain Name: JSON request**


.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/domains?name=region2.example.net
   Accept: application/json
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/json
   Content-Length: 0


**Example Filter by Fully Qualified Subdomain Name: XML request**


.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/domains?name=sub1.example.com
   Accept: application/xml
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/xml
   Content-Length: 0


**Example Filter by Fully Qualified Subdomain Name: JSON request**


.. code::

   GET https://dns.api.rackspacecloud.com/v1.0/1234/domains?name=sub1.example.com
   Accept: application/json
   X-Auth-Token: ea85e6ac-baff-4a6c-bf43-848020ea3812
   Content-Type: application/json
   Content-Length: 0


Response
--------

**Example Filter by Fully Qualified domain Name: XML response**


.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/xml
   Content-Length: 371

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <domains totalEntries="114" xmlns:ns2="http://www.w3.org/2005/Atom" xmlns="http://docs.rackspacecloud.com/dns/api/v1.0" xmlns:ns3="http://docs.rackspacecloud.com/dns/api/management/v1.0">
       <domain id="2725352" name="region2.example.net" updated="2011-06-23T20:21:06Z" created="2011-06-23T19:24:27Z"/>
   </domains>


**Example Filter by Fully Qualified domain Name: JSON response**


.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/json
   Content-Length: 202

   {
     "domains" : [ {
       "name" : "region2.example.net",
       "id" : 2725352,
       "updated" : "2011-06-23T20:21:06.000+0000",
       "created" : "2011-06-23T19:24:27.000+0000"
     } ],
     "totalEntries" : 114
   }

**Example Filter by Fully Qualified Subdomain Name: XML response**


.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/xml
   Content-Length: 435

   <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <domains totalEntries="114" xmlns:ns2="http://www.w3.org/2005/Atom" xmlns="http://docs.rackspacecloud.com/dns/api/v1.0" xmlns:ns3="http://docs.rackspacecloud.com/dns/api/management/v1.0">
       <domain id="2725257" name="sub1.example.com" emailAddress="sample@rackspace.com" updated="2011-06-23T03:09:34Z" created="2011-06-23T03:09:33Z" comment="1st sample subdomain"/>
   </domains>


**Example Filter by Fully Qualified Subdomain Name: JSON response**


.. code::

   Status: 200 OK
   Date: Thu, 28 Jul 2011 21:54:21 GMT
   X-API-VERSION: 1.0.17
   Content-Type: application/json
   Content-Length: 284

   {
     "domains" : [ {
       "name" : "sub1.example.com",
       "id" : 2725257,
       "comment" : "1st sample subdomain",
       "updated" : "2011-06-23T03:09:34.000+0000",
       "emailAddress" : "sample@rackspace.com",
       "created" : "2011-06-23T03:09:33.000+0000"
     } ],
     "totalEntries" : 114
   }

