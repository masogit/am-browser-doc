## Upgrade/Re-install

HPE updates the installation files once a new version is available. The steps to upgrade/re-install:

1. We recommend that you back up the settings and data although the following files will not be overwritten during upgrade.
    - File <am-browser-rest>\websvc\package.properties
    - File <am-browser>\am-browser-config.properties
    - Folder <am-browser>\db
    - Tomcat <am-browser-rest>\apache-tomcat-8.0.36\conf\server.xml if it is modified.
1. Copy files. Unzip the new package to the correspondent folders to overwrite the old files.

> If you try to deploy REST server war again, make sure that you unregister the previous service and register new service again.

## Migrate file DB to MongoDB

AM Browser 1.1 supports both file DB and MongoDB to store the configuration data. Also supports migrate data from file DB to MongoDB.

Ensure configure correct connection parameter for both file DB folder and MongoDB, reference chapter [Configuration](configuration/#database-configuration). Run below script by administrator or root right:

- `db_migrate.bat` in window package
- `db_migrate.sh` in linux package

*Below are the out lins from command*
```
info: [Migrating] Migrating from file to mongodb
info: [Migrating] Loading data from folder: ./db
info: [Migrating] Exporting collection: report, records: 1
info: [Migrating] Exporting collection: wall, records: 3
info: [Migrating] Exporting collection: view, records: 12
info: [Migrating] Exporting collection: aql, records: 26
info: [Migrating] Connecting mongodb: mongodb://localhost:27017/amb
info: [Migrating] Mongodb localhost connected
info: [Migrating] 42 record(s) already be imported successfully.
```

> Not support MongoDB migrate to file DB
