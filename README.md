cloudflash-firewall 
===================

Shorewall Central Administrative Server : 
----------------------------------------

Shorewall is a gateway/firewall/router/server/'standalone system' configuration tool for GNU/Linux systems. it is a high-level tool for configuring Netfilter on firewall requirements using entries in a set of configuration files. Shorewall has the capability to compile a Shorewall configuration and produce a runnable firewall program script. The script is a complete program which can be placed on a system with Shorewall-Lite installed and can serve as the firewall creation script for that system(Shorewall Lite), Shorewall is not a daemon/process.

Shorewall-lite(clients):
------------------------

Shorewall Lite is a companion product to Shorewall and is designed to allow you to maintain all Shorewall configuration information on a single system within our network. Also called as firewall system.

Shorewall supports JSON data serialization format. The format for both the request and the response should be specified by using the Content-Type header, the Accept header.

*List of APIs :*
----------------

<table>
  <tr>
    <th>Verb</th><th>URI</th><th>Description</th>
  </tr>
  <tr>
    <td>POST</td><td>/shorewall/server/:group/conf</td><td>Create a new shorewall.conf file configuarations for shorewall in VCG</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/:group/conf</td><td>Describes an installed shorewall.conf file configuarations in VCG </td>
  </tr>
  <tr>
    <td>DELETE</td><td>/shorewall/server/:group/conf</td><td>Delete an installed shorewall.conf file configuarations in VCG </td>
  </tr>
  <tr>
    <td>POST</td><td>/shorewall/server/:group/:entity/:entityid</td><td>Create a new shorewall zones, interfaces, policy, rules & routestopped configuartions for shorewall in VCG</td>
  </tr>
  <tr>
      <td>GET</td><td>/shorewall/server/:group/:entity/:entityid</td><td>Describes the configurations of the shorewall files and DB by shorewall ID </td>
  </tr>
  <tr>
    <td>DELETE</td><td>/shorewall/server/:group/:entity/:entityid</td><td>Delete configurations for shorewall files and DB  by shorewall ID</td>
  </tr>  
  <tr>
    <td>POST</td><td>/shorewall/server/:group/:action</td><td>To compile(build/rebuild) for firewall, firewall.conf files and create capabilities file for clients  in shorewall server</td>
  </tr>
  <tr>
    <td>POST</td><td>/shorewall/capabilities/server/:group</td><td>Get the capabilities configs from  orchestration in shorewall server</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/firewall/:group/scripts</td><td>To get firewall and firewall.conf files from shorewall server to orchestration</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/client/capabilities/:group</td><td>To get the capabilities file from shorewall-lite clients to orchestration </td>
  </tr>
  <tr>
    <td>POST</td><td>/shorewall/firewallfiles/client</td><td>Describes to get the firewall and firewall.conf files from orchestration to shorewall-lite clients</td>
  </tr>
  <tr>
    <td>POST</td><td>/shorewall/client/:group/:action</td><td>To Start/restart/status/clear the firewall service on VCG</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/:group/:entity/:id</td><td>Describes an installed shorewall configuartion service in VCG by service ID</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/:group/conf</td><td>Describes an installed  shorewall.conf configuartion service in VCG</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/:group/:entity</td><td>Describes the installed shorewall files configuartions of respective clients</td>
  </tr>
  <tr>
    <td>GET</td><td>/shorewall/server/:group</td><td>Describes the installed shorewall configuartion of a shorewall-lite client</td>
  </tr>
  <tr>
    <td>DELETE</td><td>/shorewall/server/:group/conf</td><td>Deletes the configurations of shorewall.conf with respective client group</td>
  </tr>
  <tr>
    <td>DELETE</td><td>/shorewall/server/:group/:entity/:id</td><td>Deletes the configurations of shorewall.conf with respective shorewall service ID</td>
  </tr>


</table>


Shorewall  Configuration API's:
--------------------------------

  1. POST /shorewall/server/:group/conf
  2. POST /shorewall/server/:group/policy/:id
  3. POST /shorewall/server/:group/rules/:id
  4. POST /shorewall/server/:group/zones/:id
  5. POST /shorewall/server/:group/interfaces/:id
  6. POST /shorewall/server/:group/routestopped/:id 

POST API :
----------

**POST  /shorewall/server/:group/conf**

Conf API will configure the shorewall.conf file, which is a global configuration file for shorewall, This file sets options that apply to Shorewall as a whole.

**Describe Service:**

    Verb  URI                                             Description
    POST  /shorewall/server/:group/conf                   Creates/updates the configurations of shorewall.conf file

###Request JSON : 
  

    {
        "STARTUP_ENABLED": "Yes",
        "VERBOSITY": "1",
        "LOGFILE": "/var/log/messages",
        "STARTUP_LOG": "/var/log/shorewall-init.log",
        "LOG_VERBOSITY": "2",
        "LOGFORMAT": "Shorewall:%s:%s:",
        "LOGTAGONLY": "No",
        "LOGRATE": "",
        "LOGBURST": "",
        "LOGALLNEW": "",
        "BLACKLIST_LOGLEVEL": "",
        "MACLIST_LOG_LEVEL": "info",
        "TCP_FLAGS_LOG_LEVEL": "info",
        "SMURF_LOG_LEVEL": "info",
        "LOG_MARTIANS": "Yes",
        "IPTABLES": "",
        "IP": "",
        "TC": "",
        "IPSET": "",
        "PERL": "/usr/bin/perl",
        "PATH": "/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin",
        "SHOREWALL_SHELL": "/bin/sh",
        "SUBSYSLOCK": "",
        "MODULESDIR": "",
        "CONFIG_PATH": "/etc/shorewall:/usr/share/shorewall",
        "RESTOREFILE": "",
        "IPSECFILE": "zones",
        "LOCKFILE": "",
        "DROP_DEFAULT": "Drop",
        "REJECT_DEFAULT": "Reject",
        "ACCEPT_DEFAULT": "none",
        "QUEUE_DEFAULT": "none",
        "NFQUEUE_DEFAULT": "none",
        "RSH_COMMAND": "'ssh ${root}@${system} ${command}'",
        "RCP_COMMAND": "'scp ${files} ${root}@${system}:${destination}'",
        "IP_FORWARDING": "Keep",
        "ADD_IP_ALIASES": "No",
        "ADD_SNAT_ALIASES": "No",
        "RETAIN_ALIASES": "No",
        "TC_ENABLED": "Internal",
        "TC_EXPERT": "No",
        "TC_PRIOMAP": "2 3 3 3 2 3 1 1 2 2 2 2 2 2 2 2",
        "CLEAR_TC": "Yes",
        "MARK_IN_FORWARD_CHAIN": "No",
        "CLAMPMSS": "No",
        "ROUTE_FILTER": "Yes",
        "DETECT_DNAT_IPADDRS": "No",
        "MUTEX_TIMEOUT": "60",
        "ADMINISABSENTMINDED": "Yes",
        "BLACKLISTNEWONLY": "Yes",
        "DELAYBLACKLISTLOAD": "No",
        "MODULE_SUFFIX": "ko",
        "DISABLE_IPV6": "No",
        "BRIDGING": "No",
        "DYNAMIC_ZONES": "No",
        "PKTTYPE": "Yes",
        "NULL_ROUTE_RFC1918": "No",
        "MACLIST_TABLE": "filter",
        "MACLIST_TTL": "",
        "SAVE_IPSETS": "No",
        "MAPOLDACTIONS": "No",
        "FASTACCEPT": "No",
        "IMPLICIT_CONTINUE": "No",
        "HIGH_ROUTE_MARKS": "No",
        "USE_ACTIONS": "Yes",
        "OPTIMIZE": "0",
        "EXPORTPARAMS": "Yes",
        "EXPAND_POLICIES": "Yes",
        "KEEP_RT_TABLES": "No",
        "DELETE_THEN_ADD": "Yes",
        "MULTICAST": "No",
        "DONT_LOAD": "",
        "AUTO_COMMENT": "Yes",
        "MANGLE_ENABLED": "Yes",
        "USE_DEFAULT_RT": "No",
        "RESTORE_DEFAULT_ROUTE": "Yes",
        "AUTOMAKE": "No",
        "WIDE_TC_MARKS": "No",
        "TRACK_PROVIDERS": "No",
        "ZONE2ZONE": "2",
        "ACCOUNTING": "Yes",
        "DYNAMIC_BLACKLIST": "Yes",
        "OPTIMIZE_ACCOUNTING": "No",
        "LOAD_HELPERS_ONLY": "No",
        "REQUIRE_INTERFACE": "No",
        "FORWARD_CLEAR_MARK": "Yes",
        "BLACKLIST_DISPOSITION": "DROP",
        "MACLIST_DISPOSITION": "REJECT",
        "TCP_FLAGS_DISPOSITION": "DROP"
    } 
  

###Response JSON :

    {
       "id": "client2",
       "entityName": "shorewall",
       "group": "client2",
       "config":
       {
            "STARTUP_ENABLED": "Yes",
            "VERBOSITY": "1",
            "LOGFILE": "/var/log/messages",
            "STARTUP_LOG": "/var/log/shorewall-init.log",
            "LOG_VERBOSITY": "2",
            "LOGFORMAT": "Shorewall:%s:%s:",
            "LOGTAGONLY": "No",
            "LOGRATE": "",
            "LOGBURST": "",
            "LOGALLNEW": "",
            "BLACKLIST_LOGLEVEL": "",
            "MACLIST_LOG_LEVEL": "info",
            "TCP_FLAGS_LOG_LEVEL": "info",
            "SMURF_LOG_LEVEL": "info",
            "LOG_MARTIANS": "Yes",
            "IPTABLES": "",
            "IP": "",
            "TC": "",
            "IPSET": "",
            "PERL": "/usr/bin/perl",
            "PATH": "/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin",
            "SHOREWALL_SHELL": "/bin/sh",
            "SUBSYSLOCK": "",
            "MODULESDIR": "",
            "CONFIG_PATH": "/etc/shorewall:/usr/share/shorewall:/config/shorewall/:group",
            "RESTOREFILE": "",
            "IPSECFILE": "zones",
            "LOCKFILE": "",
            "DROP_DEFAULT": "Drop",
            "REJECT_DEFAULT": "Reject",
            "ACCEPT_DEFAULT": "none",
            "QUEUE_DEFAULT": "none",
            "NFQUEUE_DEFAULT": "none",
            "RSH_COMMAND": "'ssh ${root}@${system} ${command}'",
            "RCP_COMMAND": "'scp ${files} ${root}@${system}:${destination}'",
            "IP_FORWARDING": "Keep",
            "ADD_IP_ALIASES": "No",
            "ADD_SNAT_ALIASES": "No",
            "RETAIN_ALIASES": "No",
            "TC_ENABLED": "Internal",
            "TC_EXPERT": "No",
            "TC_PRIOMAP": "2 3 3 3 2 3 1 1 2 2 2 2 2 2 2 2",
            "CLEAR_TC": "Yes",
            "MARK_IN_FORWARD_CHAIN": "No",
            "CLAMPMSS": "No",
            "ROUTE_FILTER": "Yes",
            "DETECT_DNAT_IPADDRS": "No",
            "MUTEX_TIMEOUT": "60",
            "ADMINISABSENTMINDED": "Yes",
            "BLACKLISTNEWONLY": "Yes",
            "DELAYBLACKLISTLOAD": "No",
            "MODULE_SUFFIX": "ko",
            "DISABLE_IPV6": "No",
            "BRIDGING": "No",
            "DYNAMIC_ZONES": "No",
            "PKTTYPE": "Yes",
            "NULL_ROUTE_RFC1918": "No",
            "MACLIST_TABLE": "filter",
            "MACLIST_TTL": "",
            "SAVE_IPSETS": "No",
            "MAPOLDACTIONS": "No",
            "FASTACCEPT": "No",
            "IMPLICIT_CONTINUE": "No",
            "HIGH_ROUTE_MARKS": "No",
            "USE_ACTIONS": "Yes",
            "OPTIMIZE": "0",
            "EXPORTPARAMS": "Yes",
            "EXPAND_POLICIES": "Yes",
            "KEEP_RT_TABLES": "No",
            "DELETE_THEN_ADD": "Yes",
            "MULTICAST": "No",
            "DONT_LOAD": "",
            "AUTO_COMMENT": "Yes",
            "MANGLE_ENABLED": "Yes",
            "USE_DEFAULT_RT": "No",
            "RESTORE_DEFAULT_ROUTE": "Yes",
            "AUTOMAKE": "No",
            "WIDE_TC_MARKS": "No",
            "TRACK_PROVIDERS": "No",
            "ZONE2ZONE": "2",
            "ACCOUNTING": "Yes",
            "DYNAMIC_BLACKLIST": "Yes",
            "OPTIMIZE_ACCOUNTING": "No",
            "LOAD_HELPERS_ONLY": "No",
            "REQUIRE_INTERFACE": "No",
            "FORWARD_CLEAR_MARK": "Yes",
            "BLACKLIST_DISPOSITION": "DROP",
            "MACLIST_DISPOSITION": "REJECT",
            "TCP_FLAGS_DISPOSITION": "DROP"
        } 
  
    }  



DELETE API:
-----------

    Verb   URI                                             Description
    DELETE /shorewall/server/:group/conf                   Deletes the configurations on shorewall.conf file

###Request Header:

DELETE /shorewall/server/:group/conf

Note: The Delete request does not require a message body. on success returns JSON data with the shorewall configuartions deleted on VCG. with deleted as true, Each delete shorewall service is identified by ID
    
###Response status :

    204


GET API:
---------

###Request Header :

**Describe Service:**

    Verb  URI                                                                 Description
    GET /shorewall/server/:group/conf                                         Description of the API get configured

###Response JSON :

    [
       {
           "id": "client2",
           "config":
           {
               "STARTUP_ENABLED": "Yes",
               "VERBOSITY": "1",
               "LOGFILE": "/var/log/messages",
               "STARTUP_LOG": "/var/log/shorewall-init.log",
               "LOG_VERBOSITY": "2",
               "LOGFORMAT": "Shorewall:%s:%s:",
               "LOGTAGONLY": "No",
               "LOGRATE": "",
               "LOGBURST": "",
               "LOGALLNEW": "",
               "BLACKLIST_LOGLEVEL": "",
               "MACLIST_LOG_LEVEL": "info",
               "TCP_FLAGS_LOG_LEVEL": "info",
               "SMURF_LOG_LEVEL": "info",
               "LOG_MARTIANS": "Yes",
               "IPTABLES": "",
               "IP": "",
               "TC": "",
               "IPSET": "",
               "PERL": "/usr/bin/perl",
               "PATH": "/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin",
               "SHOREWALL_SHELL": "/bin/sh",
               "SUBSYSLOCK": "",
               "MODULESDIR": "",
               "CONFIG_PATH": "/etc/shorewall:/usr/share/shorewall:/config/shorewall/:group",
               "RESTOREFILE": "",
               "IPSECFILE": "zones",
               "LOCKFILE": "",
               "DROP_DEFAULT": "Drop",
               "REJECT_DEFAULT": "Reject",
               "ACCEPT_DEFAULT": "none",
               "QUEUE_DEFAULT": "none",
               "NFQUEUE_DEFAULT": "none",
               "RSH_COMMAND": "'ssh ${root}@${system} ${command}'",
               "RCP_COMMAND": "'scp ${files} ${root}@${system}:${destination}'",
               "IP_FORWARDING": "Keep",
               "ADD_IP_ALIASES": "No",
               "ADD_SNAT_ALIASES": "No",
               "RETAIN_ALIASES": "No",
               "TC_ENABLED": "Internal",
               "TC_EXPERT": "No",
               "TC_PRIOMAP": "2 3 3 3 2 3 1 1 2 2 2 2 2 2 2 2",
               "CLEAR_TC": "Yes",
               "MARK_IN_FORWARD_CHAIN": "No",
               "CLAMPMSS": "No",
               "ROUTE_FILTER": "Yes",
               "DETECT_DNAT_IPADDRS": "No",
               "MUTEX_TIMEOUT": "60",
               "ADMINISABSENTMINDED": "Yes",
               "BLACKLISTNEWONLY": "Yes",
               "DELAYBLACKLISTLOAD": "No",
               "MODULE_SUFFIX": "ko",
               "DISABLE_IPV6": "No",
               "BRIDGING": "No",
               "DYNAMIC_ZONES": "No",
               "PKTTYPE": "Yes",
               "NULL_ROUTE_RFC1918": "No",
               "MACLIST_TABLE": "filter",
               "MACLIST_TTL": "",
               "SAVE_IPSETS": "No",
               "MAPOLDACTIONS": "No",
               "FASTACCEPT": "No",
               "IMPLICIT_CONTINUE": "No",
               "HIGH_ROUTE_MARKS": "No",
               "USE_ACTIONS": "Yes",
               "OPTIMIZE": "0",
               "EXPORTPARAMS": "Yes",
               "EXPAND_POLICIES": "Yes",
               "KEEP_RT_TABLES": "No",
               "DELETE_THEN_ADD": "Yes",
               "MULTICAST": "No",
               "DONT_LOAD": "",
               "AUTO_COMMENT": "Yes",
               "MANGLE_ENABLED": "Yes",
               "USE_DEFAULT_RT": "No",
               "RESTORE_DEFAULT_ROUTE": "Yes",
               "AUTOMAKE": "No",
               "WIDE_TC_MARKS": "No",
               "TRACK_PROVIDERS": "No",
               "ZONE2ZONE": "2",
               "ACCOUNTING": "Yes",
               "DYNAMIC_BLACKLIST": "Yes",
               "OPTIMIZE_ACCOUNTING": "No",
               "LOAD_HELPERS_ONLY": "No",
               "REQUIRE_INTERFACE": "No",
               "FORWARD_CLEAR_MARK": "Yes",
               "BLACKLIST_DISPOSITION": "DROP",
               "MACLIST_DISPOSITION": "REJECT",
               "TCP_FLAGS_DISPOSITION": "DROP"
           }
       }
    ]


**Interface API's:** 

Interfaces API's configures the shorewall interfaces file which serves to define the firewall's network interfaces to Shorewall. The order of entries in this file is not significant in determining zone composition.



**POST /shorewall/server/:group/interfaces/:id**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/server/:group/interfaces/:id          Configures the net zone interfaces to apply rules 


###Request JSON:

    {
        "ZONE": "net",
        "INTERFACE": "eth0",
        "BROADCAST": "detect",
        "OPTIONS": "dhcp,tcpflags,logmartians,nosmurfs"
    }

###Response JSON :

    {
       "id": ":id",
       "entityName": "interfaces",
       "group": ":group",
       "config":
       {
           "ZONE": "net",
           "INTERFACE": "eth0",
           "BROADCAST": "detect",
           "OPTIONS": "dhcp,tcpflags,logmartians,nosmurfs"
       }
    }

**GET /shorewall/server/:group/interfaces/:id**

**Describe Service:**

    Verb  URI                                             Description
    GET   /shorewall/server/:group/interfaces/:id         Configures the net zone interfaces to apply rules 


###Response JSON :

    {
       "id": ":id",
       "entityName": "interfaces",
       "group": ":group",
       "config":
       {
           "ZONE": "net",
           "INTERFACE": "eth0",
           "BROADCAST": "detect",
           "OPTIONS": "dhcp,tcpflags,logmartians,nosmurfs"
       }
    }

    
    
**ZONES API :**   
    
Creates zones configurations files entry for zones, Zones 4 API"s available 
API's configures the zones file which declares our network zones. we can specify the hosts in each zone through entries in interfaces file or hosts

  1. /shorewall/server/:group/zones/:id

**POST /shorewall/server/:group/zones/:id**

**Describe Service:**

    Verb  URI                                             Description
    POST  /shorewall/server/:group/zones/:id              Configures the firewall zones file entry

###Request JSON:

    {
        "ZONES": "$FW",
        "TYPE": "firewall",
        "OPTIONS": "",
        "IN-OPTIONS": "",
        "OUT-OPTIONS": ""
    }

###Response JSON :
  
    {
       "id": ":id",
       "entityName": "zones",
       "group": ":group",
       "config":
       {
           "ZONES": "$FW",
           "TYPE": "firewall",
           "OPTIONS": "",
           "IN-OPTIONS": "",
           "OUT-OPTIONS": ""
       }
    }

**GET /shorewall/server/:group/zones/:id**

**Describe Service:**

    Verb  URI                                             Description
    GET  /shorewall/server/:group/zones/:id               Describes configurations of the firewall zones file entry


###Response JSON :
  
    {
       "id": ":id",
       "entityName": "zones",
       "group": ":group",
       "config":
       {
           "ZONES": "$FW",
           "TYPE": "firewall",
           "OPTIONS": "",
           "IN-OPTIONS": "",
           "OUT-OPTIONS": ""
       }
    }


    
**Policy API :**  

Policy API's configures the policy file, which defines the high-level policy for connections between zones defined in shorewall-zones. The order of entries in this file is important, This file determines what to do with a new connection request if we don't get a match from the rules file . For  each source/destination pair, the file is processed in order until a match is found ("all" will match any client or server).



**POST /shorewall/server/:group/policy/:id**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/server/:group/policy/:id              Creates Policy configurations files entry for policy 

###Request JSON:

    {
        "SRC_ZONE": "$FW",
        "DEST_ZONE": "net",
        "POLICY": "ACCEPT",
        "LOG_LEVEL": "info",
        "LIMIT_BURST": ""
    }

###Response JSON :
    
    {
       "id": ":id",
       "entityName": "policy",
       "group": ":group",
       "config":
       {
           "SRC_ZONE": "$FW",
           "DEST_ZONE": "net",
           "POLICY": "ACCEPT",
           "LOG_LEVEL": "info",
           "LIMIT_BURST": ""
       }
    }


**GET /shorewall/server/:group/policy/:id**

**Describe Service:**

    Verb  URI                                             Description
    GET  /shorewall/server/:group/policy/:id              Describes the configurations files entry for policy 

###Response JSON :
    
    {
       "id": ":id",
       "entityName": "policy",
       "group": ":group",
       "config":
       {
           "SRC_ZONE": "$FW",
           "DEST_ZONE": "net",
           "POLICY": "ACCEPT",
           "LOG_LEVEL": "info",
           "LIMIT_BURST": ""
       }
    }




**Rules API :**

Rules API's will create/updates rules file configurations, Entries in this rules configuration file govern connection establishment by defining exceptions to the policies layed out in shorewall-policy. By default, subsequent requests and responses are automatically allowed using connection tracking. For any particular (source,dest) pair of zones, the rules are evaluated in the order in which they appear in this file and the first terminating match is the one that determines the disposition of the request. All rules are terminating except LOG and COUNT rules.


**POST /shorewall/server/:group/rules/:id**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/server/:group/rules/:id               Creates the shorewall rules ACCEPT configuration file entry  in rules


###Request JSON:


    {
        "ACTION": "ACCEPT",
        "SOURCE_zone": "$FW",
        "DEST_zone": "net",
        "PROTO": "icmp",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }
    

###Response JSON :

    {
       "id": ":id",
       "entityName": "rules",
       "group": ":group",
       "config":
       {
           "ACTION": "ACCEPT",
           "SOURCE_zone": "$FW",
           "DEST_zone": "net",
           "PROTO": "icmp",
           "DEST_PORT": "",
           "SOURCE_PORT": "",
           "Original_DEST": "",
           "RATE_LIMIT": "",
           "User_Group": "",
           "MARK": "",
           "CONNLIMIT": "",
           "TIME": "",
           "HEADERS": "",
           "SWITCH": ""
       }
    }

    
**GET /shorewall/server/:group/rules/:id**

**Describe Service:**

    Verb  URI                                             Description    
    GET /shorewall/server/:group/rules/:id                Describes the shorewall rules ACCEPT configuration file entry  in rules

###Response JSON :

    {
       "id": ":id",
       "entityName": "rules",
       "group": ":group",
       "config":
       {
           "ACTION": "ACCEPT",
           "SOURCE_zone": "$FW",
           "DEST_zone": "net",
           "PROTO": "icmp",
           "DEST_PORT": "",
           "SOURCE_PORT": "",
           "Original_DEST": "",
           "RATE_LIMIT": "",
           "User_Group": "",
           "MARK": "",
           "CONNLIMIT": "",
           "TIME": "",
           "HEADERS": "",
           "SWITCH": ""
       }
    }
    
    
    
**POST /shorewall/rules/drop**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/drop                            Creates the shorewall rules DROP configuration file entry  in rules


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "DROP",
        "SOURCE_zone": "net",
        "DEST_zone": "$FW",
        "PROTO": "icmp",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "DROP",
            "SOURCE_zone": "net",
            "DEST_zone": "$FW",
            "PROTO": "icmp",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  


**POST /shorewall/rules/reject**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/reject                          Creates the shorewall rules REJECT configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "REJECT",
        "SOURCE_zone": "",
        "DEST_zone": "",
        "PROTO": "",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "REJECT",
            "SOURCE_zone": "",
            "DEST_zone": "",
            "PROTO": "",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  



**POST /shorewall/rules/dnat**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/dnat                            Creates the shorewall rules DNAT configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "DNAT",
        "SOURCE_zone": "",
        "DEST_zone": "",
        "PROTO": "",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "DNAT",
            "SOURCE_zone": "",
            "DEST_zone": "",
            "PROTO": "",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  



**POST /shorewall/rules/nonat**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/nonat                           Creates the shorewall rules NONAT configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "NONAT",
        "SOURCE_zone": "",
        "DEST_zone": "",
        "PROTO": "",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "NONAT",
            "SOURCE_zone": "",
            "DEST_zone": "",
            "PROTO": "",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  



**POST /shorewall/rules/queue**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/queue                           Creates the shorewall rules QUEUE configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "QUEUE",
        "SOURCE_zone": "",
        "DEST_zone": "",
        "PROTO": "",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "QUEUE",
            "SOURCE_zone": "",
            "DEST_zone": "",
            "PROTO": "",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  



**POST /shorewall/rules/nfqueue**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/rules/nfqueue                         Creates the shorewall rules NFQUEUE configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "ACTION": "NFQUEUE",
        "SOURCE_zone": "",
        "DEST_zone": "",
        "PROTO": "",
        "DEST_PORT": "",
        "SOURCE_PORT": "",
        "Original_DEST": "",
        "RATE_LIMIT": "",
        "User_Group": "",
        "MARK": "",
        "CONNLIMIT": "",
        "TIME": "",
        "HEADERS": "",
        "SWITCH": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "ACTION": "NFQUEUE",
            "SOURCE_zone": "",
            "DEST_zone": "",
            "PROTO": "",
            "DEST_PORT": "",
            "SOURCE_PORT": "",
            "Original_DEST": "",
            "RATE_LIMIT": "",
            "User_Group": "",
            "MARK": "",
            "CONNLIMIT": "",
            "TIME": "",
            "HEADERS": "",
            "SWITCH": ""
        }
    }  

**Routestopped API**

This file is used to define the hosts that are accessible when the firewall is stopped or is being stopped.

**POST /shorewall/routestopped**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/shorewall/routestopped                Creates the shorewall routestopped configuration file entry 


###Request JSON:

    {
        "commonname": "hostname of client",
        "INTERFACE": "eth0",
        "HOSTS": "",
        "OPTIONS": "",
        "PROTO": "",
        "DEST_PORTS": "",
        "SOURCE_PORTS": ""
    }

###Response JSON :

    { 
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",    
        "config":
        {
            "commonname": "hostname of client",
            "INTERFACE": "eth0",
            "HOSTS": "",
            "OPTIONS": "",
            "PROTO": "",
            "DEST_PORTS": "",
            "SOURCE_PORTS": ""
        }
    }  



    
**Start the shorewall service :**

This API  get validates Input JSON format  by schema,  check the shorewall service installed if not response with error and  check if service-id exist in DB and host name of the client to be configured else response with error, 
It downloads the capabilities files for respective client from the repository link and start the compilation of the configurations, creates firewall and firewall.conf files and copy to clients /var/lib/shorewall-lite directory  and starts the command to be executed on client 
command “/sbin/shorewall   start”

**POST /shorewall/start :**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/start                                 Start of the firewall service on shorewall-lite

###Request JSON for start:

    {
        "commonname": "hostname of client",
        "cap_file": "http://CP-url.com/capfiles/capabilities",
        "command":"/sbin/shorewall load <client IP-ADDRESS>"
    }
    
###Response JSON :

    {
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",
        "config":
        {
            "commonname": "hostname of client",
            "cap_file": "http://CP-url.com/capfiles/capabilities",
            "command":"/sbin/shorewall load <client IP-ADDRESS>"
        }
    }


**POST /shorewall/restart :**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/restart                               Restart of the firewall service on shorewall-lite


###Request JSON for restart:

    {
        "commonname": "hostname of client",
        "cap_file": "http://CP-url.com/capfiles/capabilities",
        "command":"/sbin/shorewall reload <client IP-ADDRESS>"
    }
    
    
###Response JSON :


    {
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",
        "config":
        {
            "commonname": "hostname of client",
            "cap_file": "http://CP-url.com/capfiles/capabilities",
            "command":"/sbin/shorewall reload <client IP-ADDRESS>"
        }
    }


**Status of the shorewall service :**   

Run the shorewall status command from shorewall server through ssh, It will display the firewall runningstatus of  shorewall-lite clients.
This post display the Status of  the Shorewall service running on shorewall-lite clients

**POST /shorewall/status :**

**Describe Service:**

    Verb  URI                                             Description    
    POST /shorewall/status                                Get the running status of the shorewall-lite clients

###Request JSON  for shorewall STATUS :

    {
        "commonname": "hostname of client",
        "command":"ssh root@<hostname_IP-ADDRESS>  '/sbin/shorewall-lite  status'"  
    }

###Response JSON :

    {
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",
        "commonname": "hostname of client",
        "command":"success",
        "status": 
        {
            "started": true,
            "stopped": false,
            "cleared": false,
            "result": true
        }
    }


**Stop the Shorewall service :**

Run the shorewall stop command from shorewall server through ssh, It will stops the firewall running on shorewall-lite clients.


**POST /shorewall/stop :**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/stop                                  Stop the firewall service/configurations on respective shorewall-lite clients  


###Request JSON for STOP :

    {
        "commonname": "hostname of client",
        "command": "ssh root@<hostname_IP-ADDRESS>  '/sbin/shorewall-lite stop'"
    }
    
###Response JSON :


    {
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",
        "config":
        {
            "commonname": "hostname of client",
            "command": "ssh root@<hostname_IP-ADDRESS>  '/sbin/shorewall-lite stop'"
        }
    }

**Clear the Shorewall service :**

Run the shorewall clear command from shorewall server through ssh, It will clears the firewall running configurations on shorewall-lite clients.

**POST /shorewall/clear :**

**Describe Service:**

    Verb  URI                                             Description
    POST /shorewall/clear                                 Clear the firewall service/configurations on respective shorewall-lite clients  


###Request JSON for CLEAR :

    {
        "commonname": "hostname of client",
        "command": "ssh root@<hostname_IP-ADDRESS>  '/sbin/shorewall-lite clear'"
    }
    
###Response JSON :

    {
        "id": "7b4c38ea-268d-4a46-9e5f-d09a59f7b78b",
        "config":
        {
            "commonname": "hostname of client",
            "command": "ssh root@<hostname_IP-ADDRESS>  '/sbin/shorewall-lite clear'"
        }
    }
        
    
