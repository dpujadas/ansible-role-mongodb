mongodb
=======

This role installs and configures [MongoDB](https://www.mongodb.com/), optionally using [Percona](https://www.percona.com/software/mongo-database/percona-server-for-mongodb).

Role Variables
--------------

- `mongodb_disable_thp`: Disable [THP](https://docs.mongodb.com/manual/tutorial/transparent-huge-pages/) or not (default: True)
- `mongodb_wait_for`: Wait for server to come up or not (default: True)
- `mongodb_wait_for_timeout`: Max time (in seconds) to wait for server to come up (default: '600')
- `mongodb_use_percona`: Use percona server or not (default: False)
- `mongodb_create_admin_user`: Create admin user or not (default: False)
- `mongodb_maj_version`: Major version to install, currently only '3' (default: '3')
- `mongodb_min_version`: Minor version to install, currently only '0' or '2' (default: '0')
- `mongodb_admin_user`: User with root privileges (default: 'admin')
- `mongodb_admin_pass`: Password for admin user (Ex: 'SuperSecretPass')
- `mongodb_packages`: List of packages to install (default: [''])
- `mongodb_storage_dbpath`: The directory where the mongod instance stores its data (default: '/var/lib/mongodb')
- `mongodb_storage_journal_enabled`: Enable or disable the durability journal (default: 'true')
- `mongodb_storage_engine`: The storage engine for the mongod database (Ex: 'rocksdb')
- `mongodb_systemlog_destination`: The destination to which MongoDB sends all log output (default: 'file')
- `mongodb_systemlog_path`: The path of the log file (default: '/var/log/mongodb/mongod.log')
- `mongodb_systemlog_logappend`: Append new entries to the end of the existing log (default: 'true')
- `mongodb_systemlog_logrotate`: Set the behavior for the logRotate command (default: 'rename')
- `mongodb_processmanagement_fork`: Run process in the background or not (default: 'true')
- `mongodb_processmanagement_pidfilepath`: File location to hold the process ID (default: '/var/run/mongod.pid')
- `mongodb_net_port`: TCP port for client connections (default: '27017')
- `mongodb_net_bindip`: IP address(es) that mongos or mongod binds to (default: '127.0.0.1')
- `mongodb_net_ssl_mode`: Enable or disable TLS/SSL (Ex: 'preferSSL')
- `mongodb_net_ssl_pemkeyfile`: The .pem file that contains both the TLS/SSL certificate and key (Ex: '/path/to/PEMKeyFile')
- `mongodb_security_authorization`: Enable or disable Role-Based Access Control (default: 'disabled')
- `mongodb_security_clusterauthmode`: The authentication mode used for cluster authentication (default: 'keyFile')
- `mongodb_security_keyfile`: Path to a key file that stores the shared secret that MongoDB instances use to authenticate to each other (Ex: '/path/to/keyFile')
- `mongodb_replication_oplogsizemb`: The maximum size in megabytes for the replication operation log (Ex: '2000')
- `mongodb_replication_replsetname`: The name of the replica set (Ex: 'repl-test')
- `mongodb_setparameter`: List of parameters for mongodb (default: empty list)
- `mongodb_shell`: List of mongo commands to execute (default: '{}')
- `mongodb_users`: List of users to create (default: '[]')

Example Playbook
----------------

    - hosts: servers
      roles:
        - {
          role: mongodb,
          mongodb_use_percona: True
        }

License
-------

MIT

[![Build Status](https://travis-ci.org/dpujadas/ansible-role-mongodb.svg?branch=master)](https://travis-ci.org/dpujadas/ansible-role-mongodb)
