#postman_collections
Postman Collections for accessing the Capella Space API

#Key Variables requiring user specification:#

Authentication: provide a user name and password for the associated Capella console user:
 - username
 - password

For tasking and some search calls, the following environment variables define date ranges
 - window_open
 - window_close

Updating the window_open and window_close:
 - The date format must be specified correctly. Example: 2024-01-17T20:00:00.000Z
 - The minimum date range varies by tasking tier. The open/close date range satisfy the minimum range to avoid an error.
   - urgent (at least 1 day / 24 hours)
   - priority (at least 3 days / 72 hours)
   - priority (at least 7 days / 168 hours)
 
The additional environment variables specified are used by scripts to automate invoking endpoints more efficiently. 

#Running the collection#

##Authentication##
Authentication is required before running any other request. This uses the userid/password specified in the
environment to retrieve a token. 

Run the *"Token (Login)"* request to authenticate. This is located in the Access & Entitlement folder. 
When the request returns successfully, a "Test" script runs to update the token environment variable 
with the token just returned.

All other requests are set up to use the current token from the environment variable. 

##Folder Descriptions##

Requests are organized into the following folders. 

**Access & Entitlement:** Log in, log out, and get user profile information.
**Catalog:** Search and locate imagery in the Capella archive
**Tasking:** Make single and repeat tasking requests, check tasking status, check satellite access to a target
**Data Access:** place data orders and check order status.
**AOIs:** create and manage area of interest notification.

**Note**: many scripts use environment variables as a user convienience. For example, if an order is placed,
the last order id is stored automatically as an environment variable. Checking order status uses the 
environment variable. This environment variable can be changed as desired to override the automated updates
(e.g., to check status of other orders).

Additional API documentation is located at https://docs.capellaspace.com/
