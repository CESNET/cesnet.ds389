# cesnet.389DirectoryServer LDAP

Ansible role for installing LDAP 389DirectoryServer  on Debian 11+. It supports:
* installing a single server with Perun schemas
* installing a **supplier** replica server
* installing a **consumer** replica server
* activating plugins :
                         **memberOf overlay**  -  for consistent memberOf attribute of users
                         **referential-integrity**  -  This plugin ensures the integrity of the directory database. When objects are deleted or moved, the    "referentialintegrity" plugin update or update records of these objects in other records to avoid inconsistencies.
                         **contentsync** -  the "contentsync" plugin is used to synchronize data between LDAP directories. It allows replication of data between multiple 389 Directory Servers or with other LDAP servers, ensuring the availability of data that corresponds to different systems.
                         **retro-changelog** -  The "retro-changelog" plugin creates and maintains a record of changes that have taken place in the directory server.


## Variables

* **ds389_server_name** - name of the server taken automatically from Ansible - using for ldapmodfiy 
* **ds389_instance_name** - name of the instance you wanna create 

* **ds389_basedn** - root directory (default: dn=base)
* **ds389_root_dn** - root dn for administrating server (default: cn=Admin)
* **ds389_root_pass** - password for root directory (default: testtest)

* **ds389_certificate_file** - path to TLS certificate
* **ds389_certificate_key_file** - path to TLS private key
* **ds389_certificate_chain_file** - path to TLS certificate chain

* **ds389_repl_pass** - password for connecting replicas
* **ds389_repl_bind_dn** - DN for bind replicas (default: cn=replication manager,cn=config )
* **ds389_set_up_consumer_replica**  - if this is True, server will set up CONSUMER server (default: True)
* **ds389_set_up_supplier_replica**  - if this is True, server will set up SUPPLIER server with replication arguments
* **ds389_replica_consumer_host** - host of CONSUMER server for SUPPLIER server and argument set up
* **ds389_replication_argument_name** - name of Replica argument


* **ds389_users** - list of users to create, keys user, password and description are required for each one

* **ds389_pass_through_authentication** - whether to configure pass-through authentication using Kerberos

* **ds389_aci_content** - access rules to be added to the default rules (default empty list)


