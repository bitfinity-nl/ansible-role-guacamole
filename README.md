Role Name
=========

Apache Guacamole is a clientless remote desktop gateway.
It supports standard protocols like VNC, RDP, and SSH.

This role will the install it  on Ubuntu. 

Requirements
------------

This role depends on:

- Ubuntu 18.04Lts AM64 (Bionic Beaver)
- MySQL server 5.7


Role Variables
--------------

The variables below can be found in the defaults/main.yml file and you can override them  in your own playbook. 

Example:

Guacamole server

-  guac_server_src
-  guac_server_tar
-  guac_server_dir
-  guac_server_dir_unpacked

Guacamole client

-  guac_client_src
-  guac_client_dst

Guacamole MySQL connector

-  guac_mysql_conn_src
-  guac_mysql_conn_dst
-  guac_mysql_conn_file
-  guac_mysql_conn_src_schema

-  guac_dbname
-  guac_dbuser
-  guac_dbpass

Guacamole LDAP connector

-  guac_ldap_conn_src
-  guac_ldap_conn_dst
-  guac_ldap_conn_file

-  guac_ldap_hostname
-  guac_ldap_port
-  guac_ldap_user_base_dn
-  guac_ldap_search_bind_dn
-  guac_ldap_search_bind_dn_pass

Oracle mysql connector java

-  guac_mysql_conn_java_src 
-  guac_mysql_conn_java_dst
-  #guac_mysql_conn_java_file

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

- My



Example Playbook
----------------


  ---
    # Title: Example Playbook

    - hosts: nl-bel-guac01
      become: true

      vars:
        # MySQL server Root credentials
        MySQL_ROOT_ACCOUNT            : root
        MySQL_ROOT_PASSWORD           : Wachtw0ord123

        # MySQL DB Account
        guac_dbname                   : 'guacamole_db'
        guac_dbuser                   : 'guacamole_user'
        guac_dbpass                   : 'Guacamole123'

        # Guacamole LDAP credentials
        guac_ldap_hostname            : 'dc01.example.local'
        guac_ldap_port                : '389'
        guac_ldap_user_base_dn        : 'ou=users,ou=example,dc=example,dc=local'
        guac_ldap_search_bind_dn      : 'cn=administrator,cn=users,dc=example,dc=local'
        guac_ldap_search_bind_dn_pass : 'YourPassword'

      roles:
        - ansible-role-mysql-server-5.7
        - ansible-role-guacamole




License
-------

GNU GPLv3

Author Information
------------------

www.bitfinity.nl


Sources
-------

Many thanks to other the authors that helped me creating this role. 

- https://guacamole.apache.org/
- https://linuxhint.com/install_autodesk_maya_ubuntu_1804/
- http://squarism.com/2015/11/01/setting-mysql-timezone/
